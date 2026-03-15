# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build & Development

```bash
# Build the site
bundle exec jekyll build

# Serve locally (no watch due to Jekyll 3.9 bug on Linux)
bundle exec jekyll serve --no-watch

# Or build + serve with Python
bundle exec jekyll build && cd _site && python3 -m http.server 4000
```

## Deployment

The site is deployed via GitHub Pages from the `main` branch of `PandaJunk/PandaJunk.github.io`. Push to `main` to trigger deployment.

```bash
git add . && git commit -m "..." && git push
```

## Architecture

This is a Jekyll-based academic homepage (based on [AcadHomepage](https://github.com/RayeRen/acad-homepage.github.io)).

### Content structure

All editable content lives in `_pages/`:
- `_pages/about.md` — English homepage (permalink: `/`)
- `_pages/about_zh.md` — Chinese homepage (permalink: `/zh/`)
- `_pages/includes/` — English content fragments (about, news, pub, edu, honors)
- `_pages/includes_zh/` — Chinese content fragments (mirrors the above)

To update content, edit the relevant fragment file in `includes/` or `includes_zh/`.

### Key configuration

- `_config.yml` — site title, author info (name, avatar, email, github, googlescholar, bio, description), repository name
- `_data/navigation.yml` — navbar links; has two sections: `main` (English) and `main_zh` (Chinese)

### Bilingual navigation

`_includes/masthead.html` detects `page.url contains '/zh'` and renders either `main` or `main_zh` nav links, plus a language toggle link (English ↔ 中文).

### Asset paths

All asset paths (`images/`, `assets/css/`, `assets/js/`) must use **absolute paths** (starting with `/`) because the Chinese pages are served from `/zh/` and relative paths would break. This applies to:
- `_includes/head.html`
- `_includes/head/custom.html`
- `_includes/scripts.html`
- `_config.yml` (avatar path)
- Any `src=` in content fragment files

### Publications

Paper entries in `_pages/includes/pub.md` use the `.paper-box` layout:
```html
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">VENUE YEAR</div><img src='/images/pub/xxx.png' alt="NAME" width="100%"></div></div>
<div class='paper-box-text' markdown="1">
[**Title**](arxiv_link)
Authors
*Venue.* [[Paper]](link) \| [[Code]](link)
</div></div>
```
Paper images go in `images/pub/`. Chinese version mirrors this in `_pages/includes_zh/pub.md` with translated titles and `[[论文]]`/`[[代码]]` labels.
