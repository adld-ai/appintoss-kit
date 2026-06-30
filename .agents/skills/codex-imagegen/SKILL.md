---
name: codex-imagegen
description: >
  Use when generating required raster store assets (app logos, dark-mode logos,
  thumbnails) for an 앱인토스 mini-app. Drives the Codex CLI `imagegen`
  capability non-interactively with the gpt-5.5 model at high reasoning effort,
  then resizes outputs to the exact Toss console dimensions. Do not use for
  screenshots — those must be captured from the real running app.
---

# Codex Imagegen Skill

This skill resolves raster store asset work through
`/Users/tonylee/abld/Product/app-in-toss/guide/resolver.md`. Use the
`ASSETS_SUBMISSION` route and treat `guide/assets.md` as the source of truth.

## When to use

- App logo (light): `app-logo-600.png` — 600×600.
- App logo (dark): `app-logo-dark-600.png` — 600×600, derived from the light
  logo per `guide/assets.md`.
- Thumbnail / hero: `thumbnail-1932x828.png` — 1932×828.

Do NOT use this skill for screenshots. Screenshots must be captured from the
real running app (`npm run dev` → browser capture at 636×1048 portrait).

## Invocation

Run Codex non-interactively with `codex exec`, the `gpt-5.5` model, and
`high` reasoning effort:

```bash
codex exec -m gpt-5.5 -c model_reasoning_effort=high \
  "<LIGHT_LOGO_PROMPT_PREFIX from guide/assets.md> App: <appName>. Primary object/action: <description>."
```

For thumbnails, request the 7:3 hero composition described in
`guide/assets.md`:

```bash
codex exec -m gpt-5.5 -c model_reasoning_effort=high \
  "<THUMBNAIL_PROMPT_PREFIX from guide/assets.md> App: <appName>. Korean app name: <koreanDisplayName>. Key sentence: <clear Korean sentence>. Illustration object/action: <description>."
```

For dark-mode logos, do not start from a fresh unrelated prompt. Use the dark
logo prompt prefix from `guide/assets.md` and explicitly reference the selected
light logo as the source image when the image generation tool supports image
editing.

## Output location

Generated images are saved under:

```text
~/.codex/generated_images/<thread-id>/<image-id>.png
```

Copy the selected output into the project's `public/` tree, then mirror it
into `submission/`:

```bash
cp ~/.codex/generated_images/<thread-id>/<image-id>.png /tmp/icon-raw.png
```

## Resize to exact dimensions

Use `sips` (macOS) to lock the final canonical dimensions before saving:

```bash
# Light logo
sips -z 600 600 /tmp/icon-raw.png --out public/logo/app-logo-600.png

# Dark logo (derive from light, do not regenerate — see toss-design-theme)
# Swap background to #191f28 and lighten component tone, then:
sips -z 600 600 /tmp/icon-dark.png --out public/logo/app-logo-dark-600.png

# Thumbnail
sips -z 828 1932 /tmp/thumb-raw.png --out public/asset/thumbnail-1932x828.png
```

Then mirror into `submission/`:

```bash
cp public/logo/app-logo-600.png      submission/logo/app-logo-600.png
cp public/logo/app-logo-dark-600.png submission/logo/app-logo-dark-600.png
cp public/asset/thumbnail-1932x828.png submission/asset/thumbnail-1932x828.png
```

## Dark-mode logo derivation

The dark-mode logo is NOT a fresh imagegen output. Derive it from the light
logo:

1. Take `public/logo/app-logo-600.png` as the source.
2. Replace the background fill with `#191f28`.
3. Lighten the Toss blue component from `#3182f6` to `#6db1fe` (or a
   comparable lighter tint) so the silhouette reads cleanly on the dark
   background.
4. Save as `public/logo/app-logo-dark-600.png` at 600×600.

This can be done with a small Python/Pillow script or an image editor; the
key constraint is that the icon motif stays the same shape and position as
the light logo.

## Validation

After generation, verify dimensions with `sips -g all` or `file`:

```bash
sips -g pixelWidth -g pixelHeight public/logo/app-logo-600.png
# expect: pixelWidth: 600, pixelHeight: 600
```

Reject any asset that is not at the exact required dimension — do not ship a
scaled or cropped substitute without re-generating.
