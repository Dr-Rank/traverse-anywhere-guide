# GASP & Traverse Anywhere user guide

**Read the illustrated guide:** https://dr-rank.github.io/traverse-anywhere-guide/

The complete guide is on one continuous page, using a printable, illustrated layout: cover, movement choices, final-release scope, grouped feature pictures, practical setup and planned extras.

## Update the guide

- Edit chapter text in `_includes/guide/`. Each file is Markdown: use `##` for headings and `**text**` for bold.
- Edit the cover, feature captions and page grouping in `index.md`.
- Replace pictures in `assets/images/`, keeping their filenames, or update their links in `index.md`. WebP keeps downloads small.
- Commit changes to `main`. GitHub Pages automatically rebuilds the site; allow a few minutes.

`_data/navigation.json` controls the contents links. `assets/style.css` controls the PDF-like layout. On phones, pages adapt to the screen; printing restores page breaks. Search reads the sections on the page automatically.

Old chapter links redirect to the matching section of the complete guide. The additional property reference remains at `property-reference.html`.

This repository contains documentation and illustrative media only. It does not distribute the plugin, Game Animation Sample, private test geometry or project assets. Product and character names remain the property of their respective owners.

## Release scope update — 15 November 2026

The guide presents CMC, GMC, Network Prediction Mover and Chaos Mover as four primary choices. GMC is a separately purchased, installed and enabled paid dependency, with GMCMotion and GMAS also required for its integration.

New chapters cover the final-release scope/status, optional-feature wizard, three slide behaviours, ragdoll/get-up/death and physical reactions, paired interactions, and planned retargeting of users' own animations. Planned setup is distinguished from completed backend qualification.

Content was reconciled against the 15 November CMC handover, 14 November NP handover, 18 October extras plan (including the 15 November retargeting addition), backend-neutral extras plan and GASP feature inventory. Broader GASP inventory items remain explicitly pending where the handover does not establish complete integration. These are internal source documents; the public guide does not distribute them or the product code.

## Expanded name and CMC support

Brand: **GASP & Traverse Anywhere**. Tagline: **First or Third Person. Your Choice of Supported Skeleton.** The logo is in `assets/images/gasp-traverse-anywhere-logo.png`; the original logo remains available for historical reference. The existing repository URL and editor labels are retained.

CMC status was reconciled with the updated 15 November handover: run 7351 passed all 22 cases without the long-frame allowance, including all three animated slides. The guide records the passing GMC/Chaos shared-change regressions and the open NP regression separately from wizard, skeleton and packaging work.
