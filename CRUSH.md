## Build, lint, and test

This is a Hugo-based static site. There are two main themes used in this project: `hugo-theme-stack` and `reveal-hugo`.
- The `hugo-theme-stack` is used for the main site.
- The `reveal-hugo` is used for slideshows.

To build the site, run `hugo`. To serve the site locally, run `hugo server`.

## File structure

- All content is located in the `content` directory.
- The main site content is in `content/post`.
- Slideshows are in `content/post/<year>/<slug>/index.md`.
- Static assets are in the `static` directory.
- Customizations to the theme are in the `assets` directory.

## Creating a new post

To create a new post, create a new file in `content/post/<year>/<slug>/index.md`. The front matter should include the following:

```
---
title: "My new post"
date: 2025-07-31T12:00:00Z
---
```

## Creating a new slideshow

To create a new slideshow, create a new file in `content/post/<year>/<slug>/index.md`. The front matter should include the following:

```
---
title: "My new slideshow"
date: 2025-07-31T12:00:00Z
layout: "reveal"
---
```

## Customizing the site

To customize the site, you can edit the files in the `assets` directory.
- To add custom CSS, edit `assets/scss/custom.scss`.
- To add custom JavaScript, edit `assets/js/custom.js`.

To customize the theme, you can edit the files in `layouts` directory.
- To customize the head, edit `layouts/partials/head/custom.html`.
- To customize the sidebar, edit `layouts/partials/sidebar/left.html`.
- To customize the audio shortcode, edit `layouts/shortcodes/audio.html`.

For more information, see the documentation for the `hugo-theme-stack` and `reveal-hugo` themes.
