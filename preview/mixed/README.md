# Private Mixed Typography Preview

This is a static, private evaluation sample, not a replacement for the homepage
or approval to publish. Do not push, deploy, or integrate it into main without
separate authorization. `noindex` is a precaution, not access control; privacy
depends on keeping this worktree unserved except on loopback.

## Open Locally

From the isolated worktree root, use an existing Python 3 installation:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

Open `http://127.0.0.1:8765/preview/mixed/`. Stop the temporary server with Ctrl+C.
Do not run this in the publicly served checkout or expose the port externally.
There is no build, package installation, or third-party runtime request.

## Scope

- The original header, Hero, and first dark offer card use the original English
  and Brazilian Portuguese copy, images, colors, borders, and internal layout.
- The card keeps its original four/two/one-column grid context, with the other
  cells empty. It is deliberately not stretched to fill the desktop sample.
  The omitted section heading and other sections are not typography targets.
  The dark sample follows the Hero, using the original section padding.
- Language buttons retain translated accessible labels, pressed state, mail
  subjects, and the existing `szero-lang` local-storage preference. English
  remains readable without JavaScript; language controls are then hidden.
- The offers link targets the sample. Links to omitted sections and the home
  logo resolve to the unchanged local `../../index.html` reference. Mail links
  retain their original behavior. No link sends visitors to a public preview.
- The full-page all-serif candidate in `../../index.html` and all existing
  artwork remain unchanged. This extraction is intentionally independent;
  no shared-site refactor or whole-site font application is included.

## Typography

The preview owns its inline styles, following the existing static-page pattern.
Source Serif 4 is used only for the Hero: weight 600, natural letter spacing,
optical sizing enabled, 3rem desktop / 2rem through the existing 680px breakpoint,
and unchanged 1.15 leading. Source Sans 3 handles all remaining HTML text,
including the 1.5rem/600/1.2 card title. Card-title tracking remains unchanged.

The full `.875/1/1.125/1.25/1.5/2/3rem` token scale is retained, equivalent to
14/16/18/20/24/32/48px at a normal 16px root. No root size is forced. This sample
uses 14px auxiliary roles, 16px body, 24px card titles, and 48px or 32px Hero;
18px and 20px roles are outside this scope. Controls remain 16px/600/1.2. Body
leading stays 1.5 and Hero-introduction leading stays 1.55. Other original
weights, line heights, tracking, margins, padding, and breakpoints are retained.
No new typography containment adjustment is included.

The two unmodified Adobe variable WOFF2 files are served locally, with explicit
200-900 weight ranges and `font-display: swap`. There is no `local()` lookup,
so an installed font cannot silently substitute for the selected web asset.
Synthetic styling is disabled. Fallback stacks remain available during loading
or failure; screenshots must wait for loaded fonts and verify rendered glyphs.
See [font origins and licenses](fonts/README.md).

## Verification Scope

Use a real browser at 1440px desktop and 390px mobile in both languages. Check
the actual rendered fonts, loaded images, controls, keyboard focus, persistence,
and text/header bounds. Check tight widths and both sides of the existing
360/680/900/1100px breakpoints. Screenshots, temporary scripts, and detailed
results belong outside this repository. Technical checks are not visual
approval or whole-site verification.
