# Traverse Anywhere user guide

**Read the illustrated guide:** https://dr-rank.github.io/traverse-anywhere-guide/

The complete guide is on one continuous page, following the 24-page PDF layout: cover, setup introduction, grouped feature pictures with captions, and practical instructions.

## Update the guide

- Edit chapter text in `_includes/guide/`. Each file is Markdown: use `##` for headings and `**text**` for bold.
- Edit the cover, feature captions and page grouping in `index.md`.
- Replace pictures in `assets/images/`, keeping their filenames, or update their links in `index.md`. WebP keeps downloads small.
- Commit changes to `main`. GitHub Pages automatically rebuilds the site; allow a few minutes.

`_data/navigation.json` controls the contents links. `assets/style.css` controls the PDF-like layout. On phones, pages adapt to the screen; printing restores page breaks. Search reads the sections on the page automatically.

Old chapter links redirect to the matching section of the complete guide. The additional property reference remains at `property-reference.html`.

This repository contains documentation and illustrative media only. It does not distribute the plugin, Game Animation Sample, private test geometry or project assets. Product and character names remain the property of their respective owners.
