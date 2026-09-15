# Website typography

## Full-Page Typography

The bilingual website owns its typography in the `:root` and shared rules in
[`index.html`](../index.html). It uses the approved mixed-family direction across
the full page, with locally served fonts and no dependencies or build step.
Keep text sizes on this scale instead of adding local near-duplicates.

| Token | rem | Default pixels | Role |
| --- | --- | --- | --- |
| `--font-aux` | .875rem | 14 | Navigation labels, kickers, numbers, tags, captions, metadata |
| `--font-body` | 1rem | 16 | Body text, footer links, all buttons, Hero introduction |
| `--font-emphasis` | 1.125rem | 18 | Company introduction and principle statement |
| `--font-subtitle` | 1.25rem | 20 | Section introductions (`.lead`) |
| `--font-card` | 1.5rem | 24 | Component headings and state progression |
| `--font-section` | 2rem | 32 | Section headings and mobile Hero |
| `--font-display` | 3rem | 48 | Desktop Hero and manifesto display |

Pixel equivalents assume the browser's default 16px root. Do not fix the root
size; rem values should respect the reader's font preference. Only the Hero
changes size at the existing 680px breakpoint. Other roles keep their token.

## Families and hierarchy

- `--serif`: "Source Serif 4", Georgia, "Times New Roman", serif for the Hero,
  section headings, and manifesto display. These editorial roles use natural
  letter spacing and automatic optical sizing. Section headings and the
  manifesto preserve their 400 weight; the Hero uses 600.
- `--sans`: "Source Sans 3", Arial, Helvetica, sans-serif for body text,
  component/card titles, navigation, controls, metadata, captions, labels,
  state progression, and the 18px/20px introductory and emphasis roles.
- Body text uses 400. Controls, labels, and component headings use 600.
  The existing bold skip link remains 700. The wordmark and artwork remain images.
- The two unmodified Adobe variable WOFF2 assets, complete OFL licenses, and
  pinned provenance are in [`assets/fonts/`](../assets/fonts/README.md). Both
  faces declare weights 200-900, use URL-only sources, preload, and
  `font-display: swap`. Synthetic styling is disabled. Fallback fonts may appear
  while the assets load; no external font service or installation is required.
- Hero leading is 1.15. Its introduction is 1.55. Body and section introductions
  use 1.5. All `.button`, `.nav-cta`, and `.lang-btn` controls share
  `600 1rem/1.2 var(--sans)`.
- Reserve 14px for auxiliary information. Ordinary prose must remain at least
  16px. No current component needs monospace.

## Containment

Keep the existing section order, colors, assets, grid breakpoints, and spacing.
The two-column Hero keeps a 390px minimum text track so long serif words in
either language fit without splitting at narrow desktop widths. The mobile
heading retains its emergency word-wrap safeguard.
The Hero clips its deliberately oversized artwork at the section boundary so it
cannot expand the mobile viewport. Its right grid track can shrink without
forcing captions past the viewport. At mobile widths, captions follow the image
in normal flow so wrapped 14px labels do not overlap it.

The tablet navigation can wrap its links within their grid cell. The mobile CTA
has a 112px cap to fit both languages at 16px. At 360px and below, it occupies a
second header row to preserve the logo, language controls, and readable CTA.

## Verification

Serve the actual `index.html` and `assets/` (including `assets/fonts/`) with a
temporary loopback HTTP server, not a development build.
Do not test or modify a publicly served checkout. Use a real browser in English
and Brazilian Portuguese; check the language buttons, translated links, reload
persistence, and keyboard focus.

Review the full page at 1440px desktop and 390px mobile. Also inspect 320, 360,
361, 680, 681, 900, 901, 1100, 1101, 1280, and 1920px to cover tight layouts and
both sides of the breakpoints. Check computed sizes and families, button leading
and weight, text bounds, horizontal overflow, loaded images, and browser errors.
Confirm that both font requests succeed and inspect actual rendered glyph fonts,
not only the computed CSS stack. Serif should render the Hero, every section
heading, and manifesto display; other HTML text should render in Sans.
Compare section order, column counts, artwork, and colors with the baseline.
Typography changes natural wrapping and section heights; it must not conceal
content or move components into unrelated layouts.

There is no build command. `git diff --check` checks patch whitespace. Browser
checks remain necessary because source searches cannot detect clipping or
language-dependent wrapping.

## Preview History

The approved header/Hero/card sample is preserved in Git commit `b287bb9` at
`preview/mixed/`. The earlier all-serif full-page candidate is in `d216183`.
The temporary preview route is removed from the production tree; the homepage
is the complete mixed-family artifact. Historical samples can be extracted to
an isolated directory for comparison without changing a publicly served checkout.
