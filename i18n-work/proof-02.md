# PROOF — OPR.99.0.1.2

Builder: dev-build@relohub-editor. 2026-10-20. Code/catalog candidate: `0d4f1a4e04a0efacc55e56875cc825099155ddc9`.
Base: upstream v7.23.0 / c606125, branch `rig/OPR.99.0.1.2`, worktree `/root/Projects/openpost-ru/.worktrees/OPR.99.0.1.2`.

## Result and verification

- `i18n-work/ru-editors.json`: exactly 5240 keys, in en.json order: 3827 video, 801 image, 612 theme. All authored manually by the builder; no translation service, network translation call, external model, or subagent used. Local scripts only stored batches, reused identical translations, assembled JSON and checked it. Context-specific overrides distinguish Frame (рамка/кадр), Light (свет/светлый), Edit (править/монтаж), Source (исходник/источник).
- Ran the mission command from this worktree:
  `node /root/Projects/relohub-openpost/ops/work/missions/openpost-ru/tools/ru-lint.mjs --en apps/web/messages/en.json --ru i18n-work/ru-editors.json --scope editors`
  Result: en5240 / ru5240, missing0, extra0, errors0. Capital Вы0, straight quotes0, punctuation0, whitespace0. Remaining warnings: Latin73 distinct, long199; all listed below.
- The lead corrected the lint tool in Editor master bf4b02c: uppercase `(S)` is a shortcut, not a plural suffix; eleven keys with URL/product/model/font names are keepAsIs. Builder did not edit the tool or evade it by altering these names. Initial13 errors were precisely those two shortcut keys and eleven keepAsIs keys; final canonical tool exits0.
- Independent exact key-order and brace-token multiset comparison passed for all5240. All parenthesized single-letter and modifier shortcuts (including `(S)` and `(B)`) retained. No bracket plurals, placeholder substitutions, straight quotes or padding tricks.
- Theme rule: 612 keys, `theme_library_workshop` = Workshop preserved as required. Excluding this explicit upstream exemption: unchanged0, multiword unchanged0. The placeholder-only preview name now uses a Russian typography separator `{name} — {scheme}` (literal placeholders unchanged). There are no untranslated theme names hidden by Cyrillic prefixes.
- `git diff --check`: PASS. Only the two allowed files under i18n-work are changed; no catalog wiring, code, deps, AGENTS, ops, push, merge, PR or deployment.
- Self-review: read each source while authoring batches; checked context-sensitive shared terms against call sites and reviewed a deterministic70-pair sample after assembly. The first30 are reproduced below for lead review. No separate model review was invoked because strings must not be sent elsewhere.

## Terminology added

One rendering throughout, with inflection and grammatical context:

| English | Russian | Notes |
|---|---|---|
| sequence | секвенция | Editing sequence; image sequence = последовательность кадров |
| source (media) | исходник | Source attribution = источник; not the post source from core glossary |
| proxy | прокси | Local reduced preview; originals stay separate |
| compound clip | составной клип | Not a group of tracks |
| composition | композиция | 2D/motion composition |
| cut / edit point | склейка | Cutting action = разрезать; cut text/pixels = вырезать |
| ripple delete/edit | удалить/монтаж со сдвигом | Subsequent clips close the gap |
| slip / slide | сдвиг исходника / сдвиг клипа | Distinguishes source timing from clip placement |
| render queue | очередь рендера | Frozen snapshots, no publication implied |
| cue | реплика | Subtitle cue; count phrased without inflection |
| easing | сглаживание | Ease in/out = плавный вход/выход |
| auto-key | автоключи | Automatic keyframe creation |
| bake | запечь | Sample editable procedural animation into keys |
| live behavior | динамическое поведение | Procedural and editable, not live publishing |
| dope sheet | экспозиционный лист | Animation timeline representation |
| grade / grading | цветокоррекция | Presets and effects |
| hue / saturation / vibrance | цветовой тон / насыщенность / сочность | Tone in short controls = тон |
| lift / gamma / gain | подъём теней / гамма / усиление | Color grading; shadow style Lift = подъём |
| scope | измерительный прибор, прибор | Histogram / waveform / vectorscope names localized |
| feather | растушёвка | Masks and edges |
| blend | наложение | Standard Russian blend-mode names |
| stroke | обводка | Not brush stroke |
| checkpoint | контрольная точка | Named recovery snapshot |
| revision | редакция | Distinct from general version history |
| manifest | манифест | Theme document, not user post |
| chrome | оболочка | App/editor chrome, not Chrome browser |
| scrim | затемняющая подложка | Overlay behind dialogs |
| focal action | главное действие | Distinct from primary = основное |
| font weight / tracking | насыщенность / межбуквенный интервал | VHS tracking = трекинг |
| shader / dither | шейдер / дизеринг | Product Dither remains Dither in explanatory copy |
| playhead | курсор воспроизведения; курсор в контексте монтажа | Full glossary meaning preserved; short controls use курсор |
| downbeat / beat | сильная доля / доля | Beat grid and markers |
| voiceover | озвучка | Recording and local synthesis |
| relink | переподключить | Missing local source recovery |

## Scope not verified

No merged ru.json, language switch, browser rendering, light/dark/phone screenshots, upstream full-catalog check, frontend tests or build: slice03 owns assembly and sandbox verification. Long-label fit is **not proven** by lint; exact retained labels below must be checked in that sandbox. No live services, AI calls or publication. This is the builder candidate, not QA acceptance.

## Reproducible random sample

Selected `random.Random(99012).sample(list(ru), 70)` in en.json key order; first30 below. The remaining40 were also reviewed locally, not used to change the sampling seed.

| Key | English | Russian |
|---|---|---|
| `video_editor_shuttle_reverse` | Reverse shuttle {speed}× | Прокрутка назад {speed}× |
| `theme_preview_calendar_title` | September | Сентябрь |
| `video_editor_project_canvas_background` | Background | Фон |
| `theme_editor_preview_fallback` | Fallback preview is on. OpenPost is showing the complete Workshop theme. | Включён резервный предпросмотр. OpenPost показывает полную тему Workshop. |
| `image_editor_checkpoint` | Checkpoint | Контрольная точка |
| `image_ai_cost_pending` | Cost pending | Стоимость ожидается |
| `image_editor_saved` | Saved | Сохранено |
| `video_editor_composition_timeline_ungroup` | Ungroup | Разгруппировать |
| `image_editor_project_reading` | Checking editable project… | Проверка редактируемого проекта… |
| `video_editor_use_saved_export` | Use saved exports in post | Использовать сохранённые экспорты в посте |
| `image_editor_import_unsafe_svg` | The SVG contains scripts, external resources, or other unsafe content. | SVG содержит скрипты, внешние ресурсы или другое небезопасное содержимое. |
| `video_editor_track_close_all_gaps` | Close all gaps | Убрать все промежутки |
| `video_editor_keyframe_sheet_mixed` | Mixed | Разные |
| `video_editor_paper_image_y` | Image Y | Изображение Y |
| `video_editor_proxy_remove` | Remove proxy | Удалить прокси |
| `video_editor_blend_group_darken` | Darken | Затемнение |
| `image_editor_gradient_diamond` | Diamond | Ромбовидный |
| `video_editor_color_delete_preset` | Delete grade preset | Удалить пресет цветокоррекции |
| `video_editor_recording_storage_stopped` | Capture stopped before local storage filled. Finish to add the verified recording to the timeline. | Захват остановлен до заполнения хранилища. Завершите, чтобы добавить проверенную запись на таймлайн. |
| `video_editor_property_padding_x` | Padding X | Отступ X |
| `video_editor_audio_eq_low_pass` | Low pass | ФНЧ |
| `video_editor_color_after` | After | После |
| `video_editor_audio_eq_gain` | Gain (dB) | Усиление (дБ) |
| `video_editor_diagnostics_source_transition` | Transition | Переход |
| `video_editor_shortcuts_command_keyframe_auto` | Toggle auto-keyframe | Переключить автоключи |
| `video_editor_quick_lossless_ready` | No video transcode. Source video and audio streams will be copied into a new file. | Без перекодирования видео. Исходные видео- и аудиопотоки будут скопированы в новый файл. |
| `image_editor_applied_to_layers` | Applied to {count} layers. | Применено к слоям: {count}. |
| `theme_editor_restore_description` | OpenPost will publish its complete manifest as a new revision and make it the active draft. Existing history stays available. | OpenPost опубликует полный манифест как новую редакцию и сделает её активным черновиком. История останется доступной. |
| `video_editor_path_draw_hint` | Click for corners, drag for curves, click the first point to close, or press Enter to keep open. | Нажимайте для углов, тяните для кривых. Нажмите первую точку для замыкания или Enter, чтобы оставить контур открытым. |
| `image_editor_load_assets_failed` | Could not load OpenPost Image Editor assets. | Не удалось загрузить файлы редактора изображений OpenPost. |

## Remaining Latin warnings — all tokens and reasons

These are original identifiers, brands, licenses, technical symbols or lexer fragments. No English UI prose remains. The canonical linter intentionally reports outside its generic allowlist; do not translate API identifiers or proper names to silence it.

| Token | Count | Reason | Keys |
|---|---:|---|---|
| A | 2 | Название клавиши / обозначение дорожки A, сохраняется | `video_editor_clear_keyframes_toolbar_hint`, `video_editor_source_no_patch` |
| ACE-Step | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_local_model_ace_step_music` |
| ASCII | 3 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_gpu_effect_gpu-ascii`, `video_editor_gpu_param_ascii_opacity`, `video_editor_gpu_option_ascii_ramp` |
| AVIF | 2 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `image_editor_import_unsupported_type`, `theme_editor_upload_image_help` |
| Access | 4 | Имя браузерного API File System Access / OffscreenCanvas | `video_editor_gate_unavailable_body`, `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_blocked_body` |
| BPM | 1 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_beat_bpm_value` |
| Base | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_transcribe_model_whisper_base` |
| Boy | 1 | Имя продукта, браузера, сервиса или набора значков | `video_editor_gpu_option_game_boy` |
| Brave | 5 | Имя продукта, браузера, сервиса или набора значков | `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_blocked_title`, `video_editor_gate_filesystem_blocked_body`, `video_editor_gate_filesystem_blocked_body`, `video_editor_gate_media_api_body` |
| CC | 1 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_audio_pack_license` |
| CGA | 1 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_gpu_option_cga` |
| CMYK | 1 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_paper_halftone_cmyk` |
| Consolas | 1 | Имя гарнитуры | `video_editor_gpu_option_consolas` |
| Console | 1 | Имя гарнитуры | `video_editor_gpu_option_lucida_console` |
| Courier | 1 | Имя гарнитуры | `video_editor_gpu_option_courier` |
| D- | 5 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_motion_empty_description`, `video_editor_motion_composition_description`, `video_editor_motion_composite_badge`, `video_editor_media_upscale_3d`, `video_editor_composition_timeline_select_composite` |
| Delete | 6 | Название клавиши / обозначение дорожки A, сохраняется | `image_editor_vertical_guide_at`, `image_editor_horizontal_guide_at`, `video_editor_ripple_delete_hint`, `video_editor_keyboard_help`, `video_editor_curves_hint`, `video_editor_transcript_read_help` |
| EV | 1 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_gpu_param_exposure_ev` |
| Edge | 13 | Имя продукта, браузера, сервиса или набора значков | `video_error_encoder_unavailable`, `video_error_cannot_fit`, `video_error_invalid_edit`, `video_editor_unsupported_body`, `video_editor_supported_guidance`, `video_editor_gate_unavailable_body`, `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_blocked_body`, `video_editor_gate_storage_blocked_body`, `video_editor_gate_media_api_body`, `video_editor_local_music_desktop_required`, `video_editor_agent_webgpu_required`, `video_editor_agent_unavailable_body` |
| Emoji | 1 | Имя набора / точное название лицензии, не переводится | `video_editor_stickers_source` |
| End | 1 | Название клавиши / обозначение дорожки A, сохраняется | `video_editor_fade_handle_keyboard` |
| Escape | 6 | Название клавиши / обозначение дорожки A, сохраняется | `image_editor_polygonal_lasso_help`, `image_editor_floating_pixels_help`, `video_editor_color_picker_instruction`, `video_editor_media_placement_ready`, `video_editor_direct_text_editor`, `video_editor_media_placement_instruction` |
| File | 4 | Имя браузерного API File System Access / OffscreenCanvas | `video_editor_gate_unavailable_body`, `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_blocked_body` |
| Fluent | 1 | Имя набора / точное название лицензии, не переводится | `video_editor_stickers_source` |
| Game | 1 | Имя продукта, браузера, сервиса или набора значков | `video_editor_gpu_option_game_boy` |
| Heroicons | 2 | Имя продукта, браузера, сервиса или набора значков | `theme_icon_pack_heroicons_outline`, `theme_icon_pack_heroicons_solid` |
| Home | 2 | Название клавиши / обозначение дорожки A, сохраняется | `video_editor_fade_handle_keyboard`, `video_editor_audio_fade_curve_keyboard` |
| Kokoro | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_local_model_kokoro_voices` |
| LFM | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_scene_split_adaptive` |
| Large | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_transcribe_model_whisper_large` |
| License | 1 | Имя набора / точное название лицензии, не переводится | `video_editor_lottiefiles_license` |
| LottieFiles | 1 | Имя продукта, браузера, сервиса или набора значков | `video_editor_lottiefiles` |
| Lucida | 1 | Имя гарнитуры | `video_editor_gpu_option_lucida_console` |
| Lucide | 1 | Имя продукта, браузера, сервиса или набора значков | `theme_icon_pack_lucide` |
| MIT | 1 | Имя набора / точное название лицензии, не переводится | `video_editor_stickers_source` |
| MOSS | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_local_model_moss_voices` |
| Microsoft | 1 | Имя набора / точное название лицензии, не переводится | `video_editor_stickers_source` |
| OffscreenCanvas | 1 | Имя браузерного API File System Access / OffscreenCanvas | `video_editor_gate_media_api_body` |
| Phosphor | 1 | Имя продукта, браузера, сервиса или набора значков | `theme_icon_pack_phosphor` |
| Simple | 1 | Имя набора / точное название лицензии, не переводится | `video_editor_lottiefiles_license` |
| Small | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_transcribe_model_whisper_small` |
| Supertonic | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_local_model_supertonic_voices` |
| System | 4 | Имя браузерного API File System Access / OffscreenCanvas | `video_editor_gate_unavailable_body`, `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_api_body`, `video_editor_gate_filesystem_blocked_body` |
| Tabler | 1 | Имя продукта, браузера, сервиса или набора значков | `theme_icon_pack_tabler` |
| Tiny | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_transcribe_model_whisper_tiny` |
| Turbo | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_transcribe_model_whisper_large` |
| VHS | 1 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_gpu_effect_gpu-vhs` |
| VP | 2 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_export_webm`, `video_editor_export_webm` |
| WOFF | 2 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `theme_editor_font_size_error`, `theme_editor_upload_font` |
| WebVTT | 1 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_caption_download_vtt` |
| assets | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_resource_arrays` |
| cdn | 1 | Часть действительного URL-примера или localhost | `video_editor_media_import_url_placeholder` |
| com | 1 | Часть действительного URL-примера или localhost | `video_editor_media_import_url_placeholder` |
| cube | 3 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_effects_choose_lut`, `video_editor_effects_lut_import_failed`, `video_editor_effects_lut_size_note` |
| dark | 2 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_supported_schemes_empty`, `theme_validation_scheme_order` |
| description | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_description` |
| example | 1 | Часть действительного URL-примера или localhost | `video_editor_media_import_url_placeholder` |
| fal | 2 | Имя продукта, браузера, сервиса или набора значков | `image_ai_unconfigured`, `image_ai_disclosure` |
| fonts | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_resource_arrays` |
| https | 1 | Часть действительного URL-примера или localhost | `video_editor_media_import_url_placeholder` |
| iconPack | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_icon_pack` |
| id | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_id` |
| light | 2 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_supported_schemes_empty`, `theme_validation_scheme_order` |
| localhost | 2 | Часть действительного URL-примера или localhost | `video_editor_gate_secure_context_body`, `video_editor_local_music_secure_context` |
| mp | 1 | Часть действительного URL-примера или localhost | `video_editor_media_import_url_placeholder` |
| name | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_name` |
| p | 2 | Формат, лицензия, единица или фрагмент обозначения (CC0, VP8/9, WOFF2, 1080p, 2D/3D) | `video_editor_project_canvas_reset`, `video_editor_export_preset_web` |
| prop | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `video_editor_expression_drop_reference` |
| revision | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_revision` |
| schemaVersion | 1 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_schema_version` |
| supportedSchemes | 2 | Буквальный ключ/значение JSON или функция prop(), нужен для исправления документа | `theme_validation_supported_schemes_empty`, `theme_validation_scheme_order` |
| v | 1 | Имя модели или её варианта, необходимо для идентификации | `video_editor_transcribe_model_whisper_large` |
| video | 1 | Часть действительного URL-примера или localhost | `video_editor_media_import_url_placeholder` |

## Remaining long-label warnings — all keys

199 labels exceed the heuristic for English strings of24 characters or less. This is **not** a fit claim. Shortened65 prior warnings without hiding actions or changing terminology. Reasons: G = required glossary/precise term; A = explicit action/object retained; S = accessibility/status description retained. All require final rendered verification in slice03, particularly narrow panels and menus. Repeated labels have the same translation unless their context differs.

| Key | English | Russian | Reason |
|---|---|---|---|
| `image_editor_merge_down` | Merge down | Объединить с нижним | G: точный термин |
| `image_editor_add_guide` | Add guide | Добавить направляющую | A: действие и объект |
| `image_editor_move_guide` | Move guide | Переместить направляющую | A: действие и объект |
| `image_editor_ellipse_select` | Ellipse select | Эллиптическое выделение | G: точный термин |
| `image_editor_drag_to_place` | Drag to place | Перетащите для размещения | A: действие и объект |
| `image_editor_drop_to_place` | Drop to place | Отпустите для размещения | G: точный термин |
| `image_editor_reset_crop` | Reset crop | Сбросить кадрирование | A: действие и объект |
| `image_editor_apply_crop` | Apply crop | Применить кадрирование | A: действие и объект |
| `image_editor_crop_move` | Move crop frame | Сдвинуть рамку кадрирования | G: точный термин |
| `image_editor_workspace_category` | Workspace | Рабочее пространство | G: точный термин |
| `image_editor_resize` | Resize | Изменить размер | G: точный термин |
| `image_editor_export_preview_retry` | Retry preview | Повторить предпросмотр | A: действие и объект |
| `image_editor_rename_page` | Rename page | Переименовать страницу | A: действие и объект |
| `image_editor_save_failed` | Save failed | Не удалось сохранить | S: полное сообщение/доступность |
| `image_editor_pasted_image` | Pasted image | Вставленное изображение | A: действие и объект |
| `image_editor_export_failed` | Export failed. | Не удалось экспортировать. | S: полное сообщение/доступность |
| `image_editor_add_page` | Add page | Добавить страницу | A: действие и объект |
| `image_editor_reorder_layer` | Drag to reorder {name} | Перетащите, чтобы переместить {name} | A: действие и объект |
| `image_editor_lock_layer` | Lock {name} | Заблокировать {name} | A: действие и объект |
| `image_editor_line_height` | Line height | Межстрочный интервал | G: точный термин |
| `image_editor_add_guide_ellipsis` | Add guide… | Добавить направляющую… | A: действие и объект |
| `image_editor_brand` | Brand | Фирменный стиль | G: точный термин |
| `video_upload_editor_title` | Edit video | Редактировать видео | G: точный термин |
| `video_upload_editor_crop_zoom` | Crop zoom | Масштаб кадрирования | G: точный термин |
| `image_editor_hue` | Hue | Цветовой тон | G: точный термин |
| `video_editor_resize_timeline` | Resize timeline | Изменить размер таймлайна | G: точный термин |
| `video_editor_save_failed` | Save failed | Не удалось сохранить | S: полное сообщение/доступность |
| `video_editor_add_media` | Add media | Добавить медиафайлы | A: действие и объект |
| `video_editor_audio_eq_title` | Parametric EQ | Параметрический эквалайзер | G: точный термин |
| `video_editor_audio_eq_preset_aria` | EQ preset | Пресет эквалайзера | S: полное сообщение/доступность |
| `video_editor_audio_eq_preset_de_mud` | De-mud | Убрать гулкость | G: точный термин |
| `video_editor_clip_mute` | Mute clip | Выключить звук клипа | A: действие и объект |
| `video_editor_clip_fade_in_seconds` | Fade in (s) | Плавное появление (с) | G: точный термин |
| `video_editor_clip_fade_out_seconds` | Fade out (s) | Плавное исчезание (с) | G: точный термин |
| `video_editor_track_mute` | Mute track | Выключить звук дорожки | A: действие и объект |
| `video_editor_track_unmute` | Unmute track | Включить звук дорожки | A: действие и объект |
| `video_editor_track_unsolo` | Unsolo track | Отключить соло дорожки | A: действие и объект |
| `video_editor_track_lock` | Lock track | Заблокировать дорожку | A: действие и объект |
| `video_editor_track_unlock` | Unlock track | Разблокировать дорожку | A: действие и объект |
| `video_editor_track_sync_unlock` | Disable sync lock | Разблокировать синхронизацию | A: действие и объект |
| `video_editor_track_group_ungroup` | Ungroup tracks | Разгруппировать дорожки | A: действие и объект |
| `video_editor_track_rename` | Rename track | Переименовать дорожку | A: действие и объект |
| `video_editor_task_saving` | Saving media | Сохранение медиафайла | A: действие и объект |
| `video_editor_play` | Play | Воспроизвести | G: точный термин |
| `video_editor_template_product` | Product demo | Демонстрация продукта | G: точный термин |
| `video_editor_tool_brand` | Brand | Фирменный стиль | G: точный термин |
| `video_editor_brand_manage` | Manage brand kit | Управление фирменным стилем | A: действие и объект |
| `video_editor_queue_pause` | Pause queue | Приостановить очередь | A: действие и объект |
| `video_editor_queue_remove` | Remove render | Удалить задачу рендера | A: действие и объект |
| `video_editor_saved_exports_retry` | Try again | Попробовать ещё раз | G: точный термин |
| `video_editor_preflight_path_smart_copy` | fast copy | быстрое копирование | G: точный термин |
| `video_editor_shortcuts_use` | Use shortcut | Использовать сочетание | A: действие и объект |
| `video_editor_smart_zoom` | Suggest focus zooms | Предложить приближения к объектам | G: точный термин |
| `video_editor_credits_copy` | Copy credits | Скопировать авторство | A: действие и объект |
| `video_editor_add_title` | Add title | Добавить заголовок | A: действие и объект |
| `video_editor_shape_use_as_mask` | Use as mask | Использовать как маску | A: действие и объект |
| `video_editor_crop` | Crop media | Кадрировать медиафайл | A: действие и объект |
| `video_editor_crop_x` | Crop left | Кадрирование слева | A: действие и объект |
| `video_editor_crop_y` | Crop top | Кадрирование сверху | A: действие и объект |
| `video_editor_crop_width` | Crop width | Ширина кадрирования | G: точный термин |
| `video_editor_audio_skimming_enable` | Enable audio skimming | Включить прослушивание при прокрутке | A: действие и объект |
| `video_editor_audio_skimming_disable` | Disable audio skimming | Выключить прослушивание при прокрутке | A: действие и объект |
| `video_editor_fade_in` | Fade in | Плавное появление | G: точный термин |
| `video_editor_fade_out` | Fade out | Плавное исчезание | G: точный термин |
| `video_editor_cloud_start` | Sync and save | Синхронизировать, сохранить | A: действие и объект |
| `video_editor_use_in_post` | Use in post | Использовать в посте | A: действие и объект |
| `video_editor_reorder_clip` | Reorder clip | Изменить порядок клипа | G: точный термин |
| `video_editor_text_preset_headline` | Headline | Крупный заголовок | G: точный термин |
| `video_editor_smooth_zoom` | Add smooth zoom | Добавить плавное приближение | A: действие и объект |
| `video_editor_smooth_zoom_punch` | Punch | Резкое приближение | G: точный термин |
| `video_editor_transition_cross_dissolve` | Cross dissolve | Перекрёстное растворение | A: действие и объект |
| `video_editor_transition_zoom_blur` | Zoom blur | Размытие с приближением | A: действие и объект |
| `video_editor_transition_preset_dissolve` | Cross dissolve | Перекрёстное растворение | A: действие и объект |
| `video_editor_transition_preset_blur_dissolve` | Blur dissolve | Растворение с размытием | G: точный термин |
| `video_editor_transition_preset_lens_warp_zoom` | Lens warp zoom | Приближение с искажением линзы | A: действие и объект |
| `video_editor_transition_preset_diamond_iris` | Diamond iris | Ромбовидная диафрагма | G: точный термин |
| `video_editor_transition_preset_hexagon_iris` | Hexagon iris | Шестиугольная диафрагма | G: точный термин |
| `video_editor_transition_preset_oval_iris` | Oval iris | Овальная диафрагма | G: точный термин |
| `video_editor_transition_preset_pentagon_iris` | Pentagon iris | Пятиугольная диафрагма | G: точный термин |
| `video_editor_transition_preset_square_iris` | Square iris | Квадратная диафрагма | G: точный термин |
| `video_editor_transition_preset_box` | Box | Прямоугольник | G: точный термин |
| `video_editor_mute_clip` | Mute clip | Выключить звук клипа | A: действие и объект |
| `video_editor_blend_hue` | Hue | Цветовой тон | G: точный термин |
| `video_editor_blend_linear_burn` | Linear Burn | Линейный затемнитель | G: точный термин |
| `video_editor_blend_linear_dodge` | Linear Dodge (Add) | Линейный осветлитель (сложение) | G: точный термин |
| `video_editor_clear_marks` | Clear in/out | Сбросить вход и выход | A: действие и объект |
| `video_editor_effects_hue_rotate` | Hue rotate | Сдвиг цветового тона | G: точный термин |
| `video_editor_color_primaries` | Primaries | Первичная коррекция | G: точный термин |
| `video_editor_color_copy_grade` | Copy grade | Скопировать цветокоррекцию | A: действие и объект |
| `video_editor_color_paste_grade` | Paste grade | Вставить цветокоррекцию | A: действие и объект |
| `video_editor_shortcuts_command_track_rename` | Rename track | Переименовать дорожку | A: действие и объект |
| `video_editor_shortcuts_command_keyframe_next` | Next keyframe | Следующий ключевой кадр | G: точный термин |
| `video_editor_keyframe_view_dopesheet` | Dope Sheet | Экспозиционный лист | G: точный термин |
| `video_editor_keyframe_easing_in_out` | Ease in/out | Плавный вход и выход | G: точный термин |
| `video_editor_keyframe_bezier_out_quart` | Out quartic | Выход четвёртой степени | G: точный термин |
| `video_editor_keyframe_bezier_in_out_cubic` | In/out cubic | Кубический вход и выход | G: точный термин |
| `video_editor_keyframe_bezier_in_out_quart` | In/out quartic | Вход и выход четвёртой степени | G: точный термин |
| `video_editor_keyframe_bezier_in_out_expo` | In/out exponential | Экспоненциальный вход и выход | G: точный термин |
| `video_editor_keyframe_bezier_in_quart` | In quartic | Вход четвёртой степени | G: точный термин |
| `video_editor_source_move_range` | Move marked source range | Переместить отмеченный диапазон исходника | A: действие и объект |
| `video_editor_source_play_in_to_out` | Play in to out | Воспроизвести от входа до выхода | G: точный термин |
| `video_editor_media_sort` | Sort media | Сортировка медиафайлов | G: точный термин |
| `video_editor_media_info` | Media info | Сведения о медиафайле | G: точный термин |
| `video_editor_monitor_volume` | Preview volume | Громкость предпросмотра | G: точный термин |
| `video_editor_monitor_muted` | Preview muted | Предпросмотр без звука | G: точный термин |
| `video_editor_monitor_mute` | Mute preview | Выключить звук предпросмотра | A: действие и объект |
| `video_editor_monitor_unmute` | Unmute preview | Включить звук предпросмотра | A: действие и объект |
| `video_editor_monitor_mute_short` | Mute | Выключить звук | A: действие и объект |
| `video_editor_transcript_search_next` | Next match | Следующее совпадение | G: точный термин |
| `video_editor_import_media` | Import media | Импортировать медиафайлы | G: точный термин |
| `video_editor_scene_split_fast` | Fast scan | Быстрое сканирование | G: точный термин |
| `video_editor_scene_analyze` | Analyze missing | Анализировать недостающие | G: точный термин |
| `video_editor_open_composer` | Open composer | Открыть редактор поста | G: точный термин |
| `video_editor_crossfade` | Add crossfade | Добавить перекрёстное затухание | A: действие и объект |
| `video_editor_local_models_loaded` | {count} resident | Загружено в память: {count} | G: точный термин |
| `video_editor_property_reset_anchor` | Reset anchor | Сбросить опорную точку | A: действие и объект |
| `video_editor_property_reset_opacity` | Reset opacity | Сбросить непрозрачность | A: действие и объект |
| `video_editor_property_line_height` | Line height | Межстрочный интервал | G: точный термин |
| `video_editor_property_tracking` | Tracking | Межбуквенный интервал | G: точный термин |
| `video_editor_text_motion_blur_in` | Blur in | Появление из размытия | G: точный термин |
| `video_editor_text_motion_wave_in` | Wave in | Появление волной | G: точный термин |
| `video_editor_text_motion_pop_out` | Pop out | Уменьшение с исчезанием | G: точный термин |
| `video_editor_text_motion_blur_out` | Blur out | Исчезание в размытии | G: точный термин |
| `video_editor_motion_fade_in` | Fade in | Плавное появление | G: точный термин |
| `video_editor_motion_pop_in` | Pop in | Появление с увеличением | G: точный термин |
| `video_editor_motion_spin_in` | Spin in | Появление с вращением | G: точный термин |
| `video_editor_motion_bounce_in` | Bounce in | Появление с отскоком | G: точный термин |
| `video_editor_motion_fade_out` | Fade out | Плавное исчезание | G: точный термин |
| `video_editor_motion_pop_out` | Pop out | Уменьшение с исчезанием | G: точный термин |
| `video_editor_lottie_theme` | Theme | Тема оформления | G: точный термин |
| `video_editor_lottiefiles_retry` | Try again | Попробовать ещё раз | G: точный термин |
| `video_editor_task_upscale` | Upscaling video | Увеличение разрешения видео | G: точный термин |
| `video_editor_gpu_effect_gpu-hue-shift` | Hue Shift | Сдвиг цветового тона | G: точный термин |
| `video_editor_gpu_effect_gpu-box-blur` | Box Blur | Прямоугольное размытие | G: точный термин |
| `video_editor_gpu_effect_gpu-zoom-blur` | Zoom Blur | Размытие с приближением | A: действие и объект |
| `video_editor_gpu_effect_gpu-pixel-sort-hq` | Pixel Sort | Сортировка пикселей | G: точный термин |
| `video_editor_gpu_effect_gpu-bulge` | Bulge/Pinch | Выпуклость/вогнутость | G: точный термин |
| `video_editor_gpu_param_pivot` | Pivot | Опорный уровень | G: точный термин |
| `video_editor_gpu_param_hue` | Hue | Цветовой тон | G: точный термин |
| `video_editor_gpu_param_lum_mix` | Lum Mix | Смешение яркости | G: точный термин |
| `video_editor_gpu_param_sat_low` | Sat Low | Низ насыщенности | G: точный термин |
| `video_editor_gpu_param_sat_high` | Sat High | Верх насыщенности | G: точный термин |
| `video_editor_gpu_param_sat_softness` | Sat Softness | Мягкость насыщенности | G: точный термин |
| `video_editor_gpu_param_line_height` | Line Height | Межстрочный интервал | G: точный термин |
| `video_editor_gpu_option_hex` | Hex | Шестиугольник | G: точный термин |
| `video_editor_text_sample_headline` | Headline | Крупный заголовок | G: точный термин |
| `video_editor_mixer_track_mute` | Mute {name} | Выключить звук {name} | A: действие и объект |
| `video_editor_agent_plan_add_title` | Add title | Добавить заголовок | A: действие и объект |
| `video_editor_agent_plan_split_time` | Split at time | Разрезать в заданное время | A: действие и объект |
| `video_editor_agent_plan_review_fillers` | Review fillers | Проверить слова-паразиты | G: точный термин |
| `video_editor_edit_preview_slip` | Slip - new / baseline | Сдвиг исходника — новое / исходное | G: точный термин |
| `video_editor_adjust_audio_fade_in` | Adjust audio fade in | Настроить плавное появление аудио | A: действие и объект |
| `video_editor_adjust_video_fade_in` | Adjust video fade in | Настроить плавное появление видео | A: действие и объект |
| `video_editor_fade_in_readout` | Fade in {seconds}s | Плавное появление {seconds} с | S: полное сообщение/доступность |
| `video_editor_composition_timeline_text_off` | Offset {frames}f | Смещение в кадрах: {frames} | G: точный термин |
| `video_editor_composition_timeline_reorder` | Reorder | Изменить порядок | G: точный термин |
| `video_editor_timeline_lock` | Lock | Заблокировать | A: действие и объект |
| `video_editor_timeline_mute` | Mute | Выключить звук | A: действие и объект |
| `video_editor_background_fg_opacity` | Foreground opacity | Непрозрачность переднего плана | G: точный термин |
| `video_editor_beat_sync_title` | Sync clips to beats | Синхронизировать клипы с ритмом | A: действие и объект |
| `video_editor_beat_sync_mode_preserve` | Keep duration | Сохранить длительность | A: действие и объект |
| `video_editor_audio_effects_reorder` | Reorder {name} | Изменить порядок {name} | G: точный термин |
| `video_editor_audio_effects_wet` | Wet | Обработанный сигнал | G: точный термин |
| `video_editor_export_format_png_sequence` | PNG sequence | Последовательность PNG | G: точный термин |
| `video_editor_export_format_jpeg_sequence` | JPEG sequence | Последовательность JPEG | G: точный термин |
| `video_editor_export_format_webp_sequence` | WebP sequence | Последовательность WebP | G: точный термин |
| `theme_editor_controls` | Controls | Элементы управления | G: точный термин |
| `theme_editor_group_controls` | Controls | Элементы управления | G: точный термин |
| `theme_editor_line_height` | Line height | Межстрочный интервал | G: точный термин |
| `theme_editor_popover` | Popover | Всплывающая панель | G: точный термин |
| `theme_editor_tracking` | Tracking | Межбуквенный интервал | G: точный термин |
| `theme_editor_type_updated` | Updated type | Типографика обновлена | G: точный термин |
| `theme_library_use_theme` | Use {name} | Использовать {name} | A: действие и объект |
| `theme_preview_scene_shell` | App shell | Оболочка приложения | G: точный термин |
| `theme_preview_item_build_log` | Build log | Дневник разработки | G: точный термин |
| `theme_token_surface_raised` | Raised surface | Приподнятая поверхность | A: действие и объект |
| `theme_token_caret` | Caret | Текстовый курсор | G: точный термин |
| `theme_token_brand` | Brand | Фирменный стиль | G: точный термин |
| `theme_token_workspace` | Workspace | Рабочее пространство | G: точный термин |
| `theme_token_scrim` | Scrim | Затемняющая подложка | G: точный термин |
| `theme_token_action_focal_hover` | Focal action hover | Главное действие при наведении | G: точный термин |
| `theme_token_action_link_hover` | Action link hover | Ссылка действия при наведении | G: точный термин |
| `theme_token_card_hover` | Card hover | Карточка при наведении | G: точный термин |
| `theme_token_chrome` | App chrome | Оболочка приложения | G: точный термин |
| `theme_token_chrome_ink` | App chrome text | Текст оболочки приложения | G: точный термин |
| `theme_token_type_body` | Body | Основной текст | G: точный термин |
| `theme_token_component_popover` | Popover | Всплывающая панель | G: точный термин |
| `theme_token_component_toolbar` | Toolbar | Панель инструментов | G: точный термин |
| `theme_value_crossfade` | Crossfade | Перекрёстное затухание | A: действие и объект |
| `video_editor_shader_aurora` | Aurora | Северное сияние | G: точный термин |
| `video_editor_paper_inner_glow` | Inner glow | Внутреннее свечение | G: точный термин |
| `video_editor_paper_opacity_range` | Opacity range | Диапазон непрозрачности | G: точный термин |
| `video_editor_quick_choice_action` | Open Quick Cut | Открыть быструю обрезку | G: точный термин |
| `video_editor_chapters_reset` | Use marker names | Использовать имена маркеров | A: действие и объект |
| `video_editor_skim_time` | Skimming | Прослушивание при прокрутке | G: точный термин |
| `image_ai_edit` | AI edit image | Править изображение с ИИ | G: точный термин |
| `image_ai_action` | Image action | Действие с изображением | G: точный термин |
| `image_ai_saving` | Saving image… | Сохранение изображения… | A: действие и объект |
| `image_ai_apply_fill` | Apply fill | Применить заполнение | A: действие и объект |
