# Website Font Assets

These assets are served with the production website: Source Serif 4 for editorial headings and the manifesto display, and Source Sans 3 for body and functional text. No system font installation is required.

Both fonts are official Adobe variable upright fonts, downloaded directly from the pinned commits below on 2026-09-15. The WOFF2 binaries are unmodified upstream files: no subsetting, conversion, recompression, instancing, or internal name changes. Only the local filenames differ. Each accompanying complete upstream `LICENSE.md` was downloaded verbatim, without text or line-ending edits.

## Source Serif 4

- Local font: `source-serif-4-roman.woff2`
- Repository: https://github.com/adobe-fonts/source-serif
- Pinned commit: https://github.com/adobe-fonts/source-serif/commit/80d3f8894c09c937bebfa9011247d2e1c79fd6f4
- Upstream path: `WOFF2/VAR/SourceSerif4Variable-Roman.ttf.woff2`
- Font download: https://raw.githubusercontent.com/adobe-fonts/source-serif/80d3f8894c09c937bebfa9011247d2e1c79fd6f4/WOFF2/VAR/SourceSerif4Variable-Roman.ttf.woff2
- Local license: `source-serif-LICENSE.md`
- License download: https://raw.githubusercontent.com/adobe-fonts/source-serif/80d3f8894c09c937bebfa9011247d2e1c79fd6f4/LICENSE.md
- Embedded family: `Source Serif 4 Variable`; subfamily: `Regular`.
- Embedded version (name ID 5): `Version 4.005;hotconv 1.1.0;makeotfexe 2.6.0`.
- Copyright: 2014 - 2023 Adobe, with Reserved Font Name 'Source'. All Rights Reserved. See the verbatim license for the complete notice and trademark statement.

## Source Sans 3

- Local font: `source-sans-3-upright.woff2`
- Repository: https://github.com/adobe-fonts/source-sans
- Pinned commit: https://github.com/adobe-fonts/source-sans/commit/87b37a2daaed80fcb8e8ccb0085c4d72ddade12e
- Upstream path: `WOFF2/VF/SourceSans3VF-Upright.ttf.woff2`
- Font download: https://raw.githubusercontent.com/adobe-fonts/source-sans/87b37a2daaed80fcb8e8ccb0085c4d72ddade12e/WOFF2/VF/SourceSans3VF-Upright.ttf.woff2
- Local license: `source-sans-LICENSE.md`
- License download: https://raw.githubusercontent.com/adobe-fonts/source-sans/87b37a2daaed80fcb8e8ccb0085c4d72ddade12e/LICENSE.md
- Embedded family: `SourceSans3VF`; subfamily: `Regular`.
- Embedded version (name ID 5): `Version 3.052;hotconv 1.1.0;makeotfexe 2.6.0`.
- License copyright: 2010-2024 Adobe, with Reserved Font Name 'Source'. All Rights Reserved. The binary's older embedded copyright (name ID 0) says 2023 Adobe; both notices are retained unchanged. See the verbatim license for the complete notice and trademark statement.

## Verified Axes

The actual downloaded WOFF2 files were opened read-only with the existing system FreeType library. Their OpenType `name`, `fvar`, and `post` tables were inspected via `FT_Load_Sfnt_Table`, without installing tools or writing decompressed fonts. Versions above are embedded binary versions, not inferred release tag names.

| Font | `fvar` axis | Minimum | Default | Maximum |
| --- | --- | ---: | ---: | ---: |
| Source Serif 4 Roman | `wght` (weight) | 200 | 400 | 900 |
| Source Serif 4 Roman | `opsz` (optical size, points) | 8 | 20 | 60 |
| Source Sans 3 Upright | `wght` (weight) | 200 | 200 | 900 |

Serif has exactly these two axes: its embedded `opsz` record directly verifies that this is the optical-size variable font, not a fixed optical-size cut. Sans has only `wght`, with no `opsz` axis. Its default of 200 is the actual `fvar` value, despite the embedded `Regular` subfamily label. Both files have `post.italicAngle = 0` and neither has an italic or slant axis.

## Integrity

All four byte sizes and Git blob SHA-1 hashes matched the pinned upstream metadata. SHA-256 checksums below were computed locally on the downloaded files; they are not upstream-published signatures.

| Local file | Bytes | SHA-256 |
| --- | ---: | --- |
| `source-serif-4-roman.woff2` | 429100 | `940a76eda1388de39d38c8e7a79bf6ea058a387faee0a9f33c8d25c6ba05e1be` |
| `source-sans-3-upright.woff2` | 170188 | `5f16566f7a40d39b339ad26be151fa5a1ab1f0c2574c7a2e619765584a1acbd8` |
| `source-serif-LICENSE.md` | 4491 | `c21d7293d87b6d7ab1d0229a2f55b77f33a7613a6a4e66f6693d68d7d8d09464` |
| `source-sans-LICENSE.md` | 4486 | `56af9b9c6715597e458284a474dc118a50a4150e9d547c70f7b4a33c3e6a9328` |

| Local file | Expected upstream Git blob SHA-1 | Local comparison |
| --- | --- | --- |
| `source-serif-4-roman.woff2` | `cca344bfa7707992bf39271ee999e385c3727de2` | MATCH |
| `source-sans-3-upright.woff2` | `96cc9fd06ceb275ec3d6103ad97c5647212c88c5` | MATCH |
| `source-serif-LICENSE.md` | `5871e1f3d1b3362453b3a1f6c493fbefdbd3dcf3` | MATCH |
| `source-sans-LICENSE.md` | `22c601b82f29fc6bb801445098c9f23ffdca4f94` | MATCH |

Git blob hashes include the Git object header (`blob <byte-length>` followed by a NUL byte), so they differ from ordinary file SHA-1 checksums. Matching these hashes verifies the font and license bytes against their pinned origins; it is not a claim of signed-release verification.

Upstream metadata used for comparison:

- Serif recursive Git tree (font and license): https://api.github.com/repos/adobe-fonts/source-serif/git/trees/80d3f8894c09c937bebfa9011247d2e1c79fd6f4?recursive=1
- Sans font metadata: https://api.github.com/repos/adobe-fonts/source-sans/contents/WOFF2/VF/SourceSans3VF-Upright.ttf.woff2?ref=87b37a2daaed80fcb8e8ccb0085c4d72ddade12e
- Sans license metadata: https://api.github.com/repos/adobe-fonts/source-sans/contents/LICENSE.md?ref=87b37a2daaed80fcb8e8ccb0085c4d72ddade12e

To repeat the local checks from this directory (these commands do not install or modify fonts):

```sh
stat --format='%n %s bytes' source-serif-4-roman.woff2 source-sans-3-upright.woff2 source-serif-LICENSE.md source-sans-LICENSE.md
sha256sum source-serif-4-roman.woff2 source-sans-3-upright.woff2 source-serif-LICENSE.md source-sans-LICENSE.md
git hash-object --no-filters source-serif-4-roman.woff2 source-sans-3-upright.woff2 source-serif-LICENSE.md source-sans-LICENSE.md
```

## License Retention

Both fonts are licensed under SIL Open Font License 1.1 (26 February 2007). Keep their respective full license files and copyright notices with any permitted redistribution.
