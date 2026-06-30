# Assets and File Organization

## Image Generation

Required raster assets such as app logos, dark-mode logos, and thumbnails must
be generated with the Codex CLI `imagegen` capability, not hand-drawn SVG/HTML
or placeholder images.

Invoke Codex non-interactively with `gpt-5.5` at high reasoning effort:

```bash
codex exec -m gpt-5.5 -c model_reasoning_effort=high \
  "generate a 600x600 16-bit pixel art app icon for <app>: <description>"
```

Generated images land under `~/.codex/generated_images/<thread-id>/`. Copy the
selected output into `public/logo/` or `public/asset/`, then mirror it into
`submission/logo/` or `submission/asset/`.

Resize to exact required dimensions with `sips`:

```bash
sips -z 600 600 <input>.png --out public/logo/app-logo-600.png
sips -z 828 1932 <input>.png --out public/asset/thumbnail-1932x828.png
```

Screenshots are the only raster assets that must not be image-generated.
Capture them from the real running app.

## Prompt Prefix Rules

Use these prompt prefixes for all generated logo and thumbnail assets. Keep the
prefix intact and append only the app-specific object, action, Korean app name,
and key sentence.

### Light Logo Prompt Prefix

```text
Create a 600x600 app logo on a pure white background. Use a clean voxel icon
style: isometric 3D block construction, crisp cube edges, visible grid-like
voxel facets, flat fills, no photorealism, no soft shadows, no gradients that
blur the pixel/voxel edges. Use the Toss key color #3182f6 as the dominant side
and edge color, with white and #e8f3ff surfaces for contrast. The icon must be
one single main voxel object only, centered, large, and readable at small size.
Do not add supporting objects, scenes, cards, arrows, badges, text, letters,
brand marks, or UI chrome.
```

### Dark Logo Prompt Prefix

```text
Edit the light logo into a 600x600 dark-mode app logo. Keep the exact same
object, voxel shape, angle, size, and position. Change only the background and
contrast colors: use #191f28 as the background, brighten the Toss blue parts
from #3182f6 to #6db1fe or a comparable clear bright blue, and lift low-contrast
white/tint surfaces so the silhouette remains readable. Do not redraw the icon
as a different object. Do not add text, letters, brand marks, or UI chrome.
```

### Thumbnail Prompt Prefix

```text
Create a 1932x828 Apps in Toss store thumbnail using a clean Toss-key-color
illustration layout. Use #3182f6 as the primary color, #e8f3ff and #f2f4f6 as
soft background fields, and #191f28 only for high-emphasis text. Use Pretendard
for all Korean typography. Layout: left half has a large clear Korean title set
as exactly two rows, with one rounded Toss-blue button or chip directly below
the title; right half has an app-explaining voxel/isometric illustration; the
Korean app name sits in the top-right corner as a small pixelated Korean
text-mark, like a voxel/pixel logo label. The illustration must show the app's
actual object/action, not generic abstract shapes. Keep the composition
spacious, friendly, high contrast, and readable at store thumbnail size. Do not
use external brand logos, NAVER text, copied campaign marks, or unsupported
claims.
```

## Icon Theme

App icons (`app-logo-600.png`, 600x600) must be rendered in a clean 16-bit pixel
art style:

- Limited palette, roughly 32 colors or fewer.
- Crisp pixel edges and flat fills.
- No photoreal gradients or soft shadows.
- Prefer the voxel/isometric treatment from the light logo prompt prefix:
  block-built form, crisp cube edges, and clear object silhouette.
- Encode the app's primary object as one single centered voxel object on a flat
  background.
- Do not add secondary props, scenes, arrows, cards, badges, or text.
- Use Toss primary `#3182f6` and tint `#e8f3ff` as the dominant accent pair.
- Do not use the Toss logo, official Toss marks, or copied campaign artwork as
  the app identity.

## Hero Thumbnail

The store thumbnail (`thumbnail-1932x828.png`, 7:3 landscape) is the app's hero
image:

- Left half: one bold Korean key sentence split into exactly two title rows.
- Under the title: one rounded CTA-style button or chip in Toss blue with short
  Korean button text.
- Right half: app-explaining voxel/isometric illustration.
- Top-right: the Korean app name as a small pixelated Korean text-mark, treated
  like a voxel/pixel logo label.
- Background: `#f2f4f6` or `#e8f3ff` gradient field with a subtle Toss blue
  accent shape.
- Keep the same icon vocabulary as the app logo so logo and thumbnail read as
  one brand system.
- The hero should reveal the app's real object or task, not a generic abstract
  background.
- Use the thumbnail prompt prefix when generating: two-row Korean title,
  rounded button, Pretendard typography for main copy, explanatory
  illustration, and pixelated Korean app-name text in the top-right corner.

## Dark-Mode App Icon

The dark-mode app logo (`app-logo-dark-600.png`) is derived from the light logo,
not regenerated from scratch:

1. Swap the background to the Toss dark surface `#191f28`.
2. Keep the inside component in the same shape and position.
3. Adjust the component's color tone so it stays clear against the dark
   background. Lighten Toss blue from `#3182f6` to `#6db1fe` or a comparable
   tint, and lift any low-contrast fills.
4. Do not invert the icon's meaning or redraw it as a different object.

## File Organization

Store all project image files under `public/` by type:

- Logos: `public/logo/`
- Real product screenshots: `public/screenshot/`
- Thumbnails and other raster assets: `public/asset/`

Store the complete console submission package under `submission/`:

- Bundle: `submission/<appName>.ait`
- Logos: `submission/logo/`
- Screenshots: `submission/screenshot/`
- Thumbnail and other raster assets: `submission/asset/`
- Metadata: `submission/inputs.md`

Use lowercase ASCII kebab-case filenames. Do not use spaces, Korean filenames,
timestamp screenshot names, or generic names for canonical files.

Required upload asset filenames:

- `app-logo-600.png`
- `app-logo-dark-600.png`
- `thumbnail-1932x828.png`
- `screenshot-<nn>-<screen-name>-636x1048.png`
- `screenshot-<nn>-<screen-name>-1504x741.png` for landscape screenshots

Keep only canonical final files. Remove duplicate staging copies such as
`assets/toss-submission/`, root-level screenshot files, and root-level `.ait`
files after `public/` and `submission/` are populated.
