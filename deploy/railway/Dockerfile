# Standalone Railway build: the repository root is the only Docker context.
FROM oven/bun:1.3.11 AS bun-toolchain
FROM docker.io/library/golang:1.26.9-alpine@sha256:cdfd4fe2da6b225d8b40c6b7a105736e548e83ff56d5d8f9394446eeb5eb84e0 AS go-toolchain
FROM node:24.17.0-bookworm-slim AS frontend-builder
RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates git gcc libc6-dev && rm -rf /var/lib/apt/lists/*
COPY --from=bun-toolchain /usr/local/bin/bun /usr/local/bin/bun
RUN ln -s /usr/local/bin/bun /usr/local/bin/bunx
COPY --from=go-toolchain /usr/local/go /usr/local/go
ENV PATH="/usr/local/go/bin:${PATH}"
WORKDIR /app
COPY . .
RUN bun install --frozen-lockfile
RUN bun run build -- frontend

# Upstream backend/runtime with local frontend output and no cache mounts.
# Railway's build variable supplies the revision; explicit COMMIT overrides it.
# Build stage for backend
FROM docker.io/library/golang:1.26.9-alpine@sha256:cdfd4fe2da6b225d8b40c6b7a105736e548e83ff56d5d8f9394446eeb5eb84e0 AS backend-builder

ARG VERSION=v7.23.0-ru.1
ARG RAILWAY_GIT_COMMIT_SHA=unknown
ARG COMMIT=${RAILWAY_GIT_COMMIT_SHA}

RUN apk add --no-cache gcc musl-dev sqlite-dev

WORKDIR /app

COPY apps/server/go.mod apps/server/go.sum ./apps/server/
RUN cd apps/server && go mod download

COPY apps/server/ ./apps/server/
# Package the frontend-owned build output at the backend embed boundary.
COPY --from=frontend-builder /app/apps/server/cmd/openpost/public/ ./apps/server/cmd/openpost/public/

RUN cd apps/server && CGO_ENABLED=1 GOOS=linux go build -buildvcs=false -ldflags="-s -w -X main.version=${VERSION} -X main.commit=${COMMIT}" -o openpost ./cmd/openpost

# Runtime stage.
FROM docker.io/library/alpine:3.24.2@sha256:294b683cb724975bec92580e1e685676bd4b50bda910ddb8c51d4cabeaec77e6 AS runtime

ARG VERSION=v7.23.0-ru.1
ARG RAILWAY_GIT_COMMIT_SHA=unknown
ARG COMMIT=${RAILWAY_GIT_COMMIT_SHA}
LABEL org.opencontainers.image.title="OpenPost" \
      org.opencontainers.image.version="${VERSION}" \
      org.opencontainers.image.revision="${COMMIT}" \
      org.opencontainers.image.source="https://github.com/getopenpost/openpost" \
      org.opencontainers.image.base.name="docker.io/library/alpine:3.24.1" \
      org.opencontainers.image.base.digest="sha256:28bd5fe8b56d1bd048e5babf5b10710ebe0bae67db86916198a6eec434943f8b"

RUN apk add --no-cache ca-certificates ffmpeg tzdata sqlite \
    'libcrypto3>=3.5.8-r0' 'libssl3>=3.5.8-r0'

RUN adduser -D -u 1000 openpost

WORKDIR /app

COPY --from=backend-builder /app/apps/server/openpost .

RUN mkdir -p /data/media /data/db && chown -R openpost:openpost /data

USER openpost

ENV OPENPOST_PORT=8080
ENV OPENPOST_EDITION=selfhost
ENV OPENPOST_DATABASE_DRIVER=sqlite
ENV OPENPOST_DATABASE_PATH=/data/db/openpost.db
ENV OPENPOST_STORAGE_DRIVER=local
ENV OPENPOST_MEDIA_PATH=/data/media
ENV OPENPOST_DIAGNOSTICS_STATE_FILE=/data/diagnostics-installation-id

EXPOSE 8080

# Container health is process liveness. Traffic and rollout gates use /ready.
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD wget --no-verbose --tries=1 --spider http://localhost:8080/api/v1/health || exit 1

STOPSIGNAL SIGTERM

CMD ["./openpost", "all"]
