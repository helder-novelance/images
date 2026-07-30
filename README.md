# Services Animations — Lottie files

Converted from the original SVG + CSS keyframe animations. Vector, transparent
background, seamless loops.

## Contents
- `lottie/light/*.json` — light-theme variants (colors from the original `:root` palette)
- `lottie/dark/*.json` — dark-theme variants (colors from the original `prefers-color-scheme: dark` palette)
- `preview.html` — open in any browser to preview all six with a light/dark toggle

| File | Canvas | Loop |
|---|---|---|
| 1-implementation.json | 680×520 | 18s |
| 2-optimization.json | 680×450 | 6s |
| 3-integration.json | 680×446 | 2.2s |
| 4-customization.json | 680×300 | 5s |
| 5-data-migration.json | 680×296 | 16.5s |
| 6-system-health-audit.json | 680×350 | 4s |

## Usage (web)
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.12.2/lottie.min.js"></script>
<div id="anim"></div>
<script>
  lottie.loadAnimation({
    container: document.getElementById('anim'),
    renderer: 'svg', loop: true, autoplay: true,
    path: 'lottie/light/1-implementation.json'
  });
</script>
```
Swap the `light`/`dark` path based on `window.matchMedia('(prefers-color-scheme: dark)')`
to reproduce the original CSS dark-mode behavior. The originals also disabled motion
under `prefers-reduced-motion` — reproduce that by not autoplaying when
`(prefers-reduced-motion: reduce)` matches.

## Notes on the conversion
- Text is exported as native Lottie text layers referencing `system-ui, sans-serif`,
  so type matches the site font in lottie-web. Native mobile players (lottie-ios /
  lottie-android) need a font registered, or ask for a glyphs-baked version.
- To make every file loop seamlessly, three periods were micro-adjusted
  (imperceptible): Implementation inner orbit 11s → 10.8s and pulse 2.4s → 2.25s;
  Data Migration wheel spin 2.64s → 2.75s and scanner beam 2.2s → 2.06s per pass.
- Colors, timings, easings, and layout otherwise match the source files 1:1.
