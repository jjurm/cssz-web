# cssz.ch

*Official website of the **Czech and Slovak Students in Zurich** association (available at [cssz.ch](https://cssz.ch/))*

Website built on [Hugo](https://gohugo.io/).

## Making changes

Changes on the `main` branch trigger the [`gh-pages` workflow](https://github.com/jjurm/cssz-web/blob/main/.github/workflows/gh-pages.yml) within GitHub Actions. This automatically builds the website into the `gh-pages` branch and publishes to [cssz.ch](https://cssz.ch/).

### Local development

If you prefer developing locally (you can preview any changes immediately and without having to commit), follow these steps:

1. Install [Hugo](https://gohugo.io/getting-started/installing/), [Node.js and npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
2. `git clone git@github.com:jjurm/cssz-web.git && cd cssz-web`
3. `git submodule init`
4. `git submodule update`
5. `npm install`
6. `hugo server -DF` to start a local server (`-DF` is to include drafts and posts dated in the future) or just `hugo -DF` to build the static website (to the `public` directory)

    The first build may take >1min (due to preprocessing a lot of high-res images which are cached for future builds).

    If you are developing locally, running `hugo server` will rebuild on any file changes, reflecting updates automatically and immediately.

## Getting Started

### Structure

- `assets` - images and other assets that need pre-processing (usually, all images are loaded from this folder, so that they can be resized, compressed, and cut as needed)
- `config.yml` - global configuration (website title, menu, metadata, other options)
- `data` - structural data shared across pages, such as board/event coordinators and their details
- `content` - contains all the content: pages, blog posts
- `static` - images and other static assets that are served without any modification (unlike `assets`)
- `themes` - the themes, defining how `content` is rendered
  - `hugo-theme-stack` - default source of structure, used if not overwritten in `themes/cssz`
  - `cssz` - overwrites the default
    - `assets` - JS and CSS code
    - `layouts` - HTML templates, HTML code and shortcodes

### Front Matter

The following properties in the front matter might be helpful:

```markdown
---
hidden_on_homepage: true  # Page is published in the list of events and the calendar, but not on the homepage
hidden_in_calendar: true  # Page is published normally, just hidden in the .ics calendar file (only for events)
hidden: true              # Page is hidden from: homepage, events list, calendar (and sitemap), but still accessible via direct link
draft: true               # Page is not published at all
pinned: true              # Page is pinned to the top of the homepage
---
```
