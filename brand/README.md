# S0 chart palette

Use this palette for independent categories in charts, reports, and presentations.
It extends S0's neutral-and-lime identity without changing the website or logos.

[`palette.json`](palette.json) is the source of truth for color values and default
category order. All values are opaque, six-digit sRGB hex colors. The file has no
runtime dependencies and is not loaded by the website.

## Categorical colors

The default order is **blue, orange, green, purple, red, cyan**. Use the first four
for a new four-category comparison. Keep an existing category's assigned color
when it appears again, even if a chart uses only a subset of the categories.

| Order | Token | Hex | RGB | Contrast on paper | Contrast on white |
| --- | --- | --- | --- | --- | --- |
| 1 | `blue` | `#3B6FB6` | 59, 111, 182 | 4.45:1 | 4.82:1 |
| 2 | `orange` | `#B8741A` | 184, 116, 26 | 3.32:1 | 3.59:1 |
| 3 | `green` | `#26826C` | 38, 130, 108 | 4.10:1 | 4.43:1 |
| 4 | `purple` | `#8064B4` | 128, 100, 180 | 4.19:1 | 4.53:1 |
| 5 | `red` | `#C4515C` | 196, 81, 92 | 3.94:1 | 4.26:1 |
| 6 | `cyan` | `#247F9E` | 36, 127, 158 | 4.00:1 | 4.33:1 |

These are medium-tone categorical hues, not a light-to-dark scale or a ranking.
They avoid the deliberate emphasis of black/lime results next to gray results.
The hues are not perceptually identical in prominence; equal-status comparisons
also need consistent mark sizes, opacity, stroke weights, and labeling.

Blue and orange form the first pair. Green and purple expand it to four without
requiring a red/green distinction. Red and cyan are additional categories, not
failure/success or cold/hot indicators. Bright yellow and brand lime are excluded
from the category cycle because they have weak contrast on S0's light surfaces
and would create a different level of emphasis.

## Core brand, unchanged

These tokens mirror the existing `:root` values in [`index.html`](../index.html).
`dark_line` in JSON corresponds to `--dark-line` in CSS. This is a reference copy;
the website still owns its existing styles. If a core brand value changes, update
the reference copy and recheck chart contrast.

| Token | Hex | Chart role |
| --- | --- | --- |
| `ink` | `#0B0C0A` | Titles, labels, axes, neutral annotations |
| `paper` | `#F2F0E9` | Default chart background |
| `white` | `#FAF9F4` | Alternate light chart panel; not pure white |
| `muted` | `#6A6861` | Secondary text, not a category |
| `line` | `#D2CFC5` | Subtle, nonessential gridlines and separators |
| `dark_line` | `#33342F` | Existing dark-surface separator token |
| `lime` | `#D7FF18` | Brand accents and explicit non-data callouts |

Keep the existing [mark](../assets/szero-mark.svg) and
[wordmark](../assets/szero-wordmark.svg). Do not recolor a logo using category
colors. Category green is distinct from brand lime.

## Chart rules

1. **Assign by identity, not outcome.** Record a name-to-color mapping once for a
   report or dashboard. Do not recolor a winner, baseline, or proposed method to
   imply priority. An independent baseline gets its own categorical color too.
2. **Keep comparisons equal-status.** Use opaque fills and consistent borders,
   line widths, and marker sizes. Do not mute several results while one gets ink
   or lime. Express a justified comparison with a labeled annotation, not an
   unexplained change in saturation.
3. **Label results, not colors.** Prefer category names beside bars and line ends;
   include values and units where practical. A legend uses actual category names,
   not “the green result.” A chart must remain interpretable without hue.
4. **Add a second encoding where needed.** For overlapping lines or points, pair
   colors with distinct dashes or marker shapes and show both in the legend. Use
   hatches for bars when labels alone do not resolve groups, particularly in
   grayscale. Provide the values in a table or accessible text equivalent.
5. **Use a light plot panel.** These fills are checked on `paper` and `white` at
   full opacity. On a dark slide, place the chart on a light panel; this is not a
   dark-theme palette. Recheck contrast on any other surface, including tints,
   photographs, transparent layers, or gradients.
6. **Keep text outside fills.** Use `ink` labels on the light panel by default.
   Category colors are not approved as normal-size text colors, and neither ink
   nor white text passes 4.5:1 on every category fill. If an inside label is
   unavoidable, give it an opaque light backing with ink text and verify it.
7. **Do not rely on touching hues.** The colors do not have 3:1 contrast with each
   other. Separate adjacent filled segments with a light gap or divider and keep
   them explicitly labeled. Avoid overlapping opaque regions that hide results.
8. **Do not cycle after six.** Use small multiples, fewer simultaneous series, or
   a labeled table. Do not recycle a hue, add arbitrary tints, or use gray/lime as
   extra independent categories. Missing data is explicitly labeled, not assigned
   an indistinguishable gray result.
9. **Use another design for quantities.** This palette is categorical, not
   sequential or diverging. Ordered magnitudes, signed differences, and status
   indicators need an explicit scale or semantic mapping and separate checks.

### Accessibility boundary

The table reports WCAG relative-luminance contrast between each full-opacity
color and each light panel, rounded to two decimals. All six exceed **3:1** on
both panels. That checks visibility against the background; it does **not**
certify a complete chart, normal-size text, pairwise hue distinction, or
color-vision accessibility. In particular, red/green and blue/purple/cyan can
become difficult to distinguish under color-vision deficiencies or projection.

Review the actual exported chart at its delivery size, in grayscale, and with
color-vision simulation where available. Labels, markers, dashes, hatches, and
an accessible table remain necessary even when a color preview looks clear.

## Reuse

The JSON separates `brand` from `categorical` so a chart cannot accidentally use
lime or grays when it requests category colors. `default_order` is explicit;
do not depend on dictionary key order. `chart_backgrounds` names supported brand
tokens. `version` identifies this palette definition; increment it when changing
color values or the category order so downstream exports can record the change.

Python, from the repository root (standard library only):

```python
import json
from pathlib import Path

palette = json.loads(Path("brand/palette.json").read_text(encoding="utf-8"))
cycle = [palette["categorical"][name] for name in palette["default_order"]]
series_names = ["Method A", "Method B", "Method C", "Method D"]
if len(series_names) > len(cycle):
    raise ValueError("Split the chart instead of recycling category colors")
series_colors = dict(zip(series_names, cycle))
background = palette["brand"]["paper"]
label_color = palette["brand"]["ink"]
# Reuse series_colors unchanged across figures, including subset figures.
```

For SVG/CSS, use the hex values directly as fills or strokes. For presentation
software, enter the RGB triplets from the table; for formats that require hex
without `#`, remove only that prefix. Do not substitute a theme's similarly named
red, green, blue, or orange. Keep chart names, values, and second encodings with
the color mapping when exporting.
