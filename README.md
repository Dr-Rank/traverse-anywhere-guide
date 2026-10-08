# Traverse Anywhere user guide

The public illustrated guide for Traverse Anywhere by Execute Games.

**Read the guide:** https://dr-rank.github.io/traverse-anywhere-guide/

## Update the guide

1. Open a page on the website and choose **Edit this page**. Sign in to GitHub.
2. Edit the Markdown text. Use `##` for headings and `**text**` for bold.
3. Preview the changes, then commit them to `main`. GitHub Pages rebuilds automatically; allow a few minutes.

To replace an illustration, upload its replacement to `assets/images/` and keep the filename, or change its link in `features.md`. Use WebP for compact images. Captions live beside the images in that page.

To add a page, copy the front matter from an existing Markdown page, give it a unique title and permalink, and add it to `_data/navigation.json`. Search includes every page marked `guide: true` automatically.

`_layouts/default.html` controls the page template; `assets/style.css` controls appearance. This site uses GitHub Pages' built-in Jekyll build, with no custom workflow or paid hosting dependency.

This repository contains documentation and illustrative media only. It does not distribute the plugin, Game Animation Sample, private test geometry or project assets. Product and character names remain the property of their respective owners.
