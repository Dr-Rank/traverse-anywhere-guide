# GASP & Traverse Anywhere user guide

**Read the illustrated guide:** https://dr-rank.github.io/traverse-anywhere-guide/

The complete guide is on one continuous page, using a printable, illustrated layout: cover, movement choices, final-release scope, grouped feature pictures, practical setup, extras, first person and a Blueprint reference.

## Update the guide

- Edit chapter text in `_includes/guide/`. Each file is Markdown: use `##` for headings and `**text**` for bold.
- Edit the cover, feature captions and page grouping in `index.md`.
- Replace pictures in `assets/images/`, keeping their filenames, or update their links in `index.md`. WebP keeps downloads small.
- Commit changes to `main`. GitHub Pages automatically rebuilds the site; allow a few minutes.

`_data/navigation.json` controls the contents links. `assets/style.css` controls the PDF-like layout. On phones, pages adapt to the screen; printing restores page breaks. Search reads the sections on the page automatically.

Old chapter links redirect to the matching section of the complete guide. The additional property reference remains at `property-reference.html`.

This repository contains documentation and illustrative media only. It does not distribute the plugin, Game Animation Sample, private test geometry or project assets. Product and character names remain the property of their respective owners.

## Tester edition — 21 November 2026

- New chapters: **The setup window**, **Copy an engine pawn into your project**, **First-person camera functions** (the six Blueprint camera functions, with an example graph) and **Blueprint reference** (traversal, ragdoll, hits, death and paired interactions).
- **Use the setup wizard** rewritten for the current wizard, with fresh screenshots of both paths (keep your pawn, create a new pawn), extras and review.
- **Make an object traversable** now covers the level editor's Make Traversable and Cull Covered Traversal Proxies commands.
- Status chapters now describe what is in this tester build; planned-only material is limited to retargeting your own animations, which is marked *Not in this build*.
- The setup labels match the editor: Ready, Action needed, Needs attention, Optional, Info and Restart needed, with Apply and Apply required changes.
