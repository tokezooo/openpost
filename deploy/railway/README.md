# Railway: build OpenPost ru from GitHub

Use repository root as build context and set
`RAILWAY_DOCKERFILE_PATH=deploy/railway/Dockerfile`. No prebuilt frontend upload or
named BuildKit context is required. Bun 1.3.11, Node 24.17.0 and Go 1.26.9 build the
frontend inside Docker; the upstream Alpine backend/runtime embeds its output.
The upstream `.dockerignore` remains unchanged.

```sh
docker build -f deploy/railway/Dockerfile \
  --build-arg RAILWAY_GIT_COMMIT_SHA="$(git rev-parse HEAD)" \
  -t openpost-ru:local .
```

`VERSION` defaults to `v7.23.0-ru.1`. `COMMIT` defaults to
`RAILWAY_GIT_COMMIT_SHA` when supplied as a build argument, otherwise `unknown`.
An explicit `--build-arg COMMIT=...` overrides it. Both binary and OCI labels use
these values. In Railway select the `relohub/prod` branch; keep runtime variables
and the persistent `/data` volume on the service. Credentials are runtime-only.

Configuration references: [Railway Dockerfiles](https://docs.railway.com/builds/dockerfiles),
[Bun Docker image](https://bun.sh/guides/ecosystem/docker).
