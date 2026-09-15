# Website typography

## Candidate Status

This document describes the preserved full-page all-serif candidate, not an
approved visual direction. The separate [private mixed preview](../preview/mixed/README.md)
evaluates Source Serif 4 in the Hero and Source Sans 3 in its header, body,
controls, and one dark card. It does not change `index.html`, authorize
publication, or extend the new typography to the whole site.

## Full-Page Reference

The bilingual website owns its typography in the `:root` and shared rules in
[`index.html`](../index.html). It has no external fonts, dependencies, or build
step. Keep text sizes on this scale instead of adding local near-duplicates.

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

- `--serif`: Georgia, "Times New Roman", serif for all website text, including
  the Hero, body, navigation, controls, and metadata. Section headings and the
  manifesto preserve their intentional 400 weight. The wordmark and artwork
  remain image assets.
- The stack uses locally available fonts; actual glyphs and wrapping depend on
  the platform's installed serif fonts. No web font download is required.
- Body text uses 400. Controls, labels, and component headings use 600. The Hero
  uses 700. The existing bold skip link remains 700.
- Hero leading is 1.15. Its introduction is 1.55. Body and section introductions
  use 1.5. All `.button`, `.nav-cta`, and `.lang-btn` controls share
  `600 1rem/1.2 var(--serif)`.
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

Serve the actual `index.html` and `assets/` with a temporary loopback HTTP server.
Do not test or modify a publicly served checkout. Use a real browser in English
and Brazilian Portuguese; check the language buttons, translated links, reload
persistence, and keyboard focus.

Review the full page at 1440px desktop and 390px mobile. Also inspect 320, 360,
361, 680, 681, 900, 901, 1100, 1101, 1280, and 1920px to cover tight layouts and
both sides of the breakpoints. Check computed sizes and families, button leading
and weight, text bounds, horizontal overflow, loaded images, and browser errors.
Compare section order, column counts, artwork, and colors with the baseline.
Typography changes natural wrapping and section heights; it must not conceal
content or move components into unrelated layouts.

There is no build command. `git diff --check` checks patch whitespace. Browser
checks remain necessary because source searches cannot detect clipping or
language-dependent wrapping.
