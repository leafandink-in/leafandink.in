# Leaf & Ink

One story a week.

## To publish a new issue

1. Add a file to `_posts/` named `YYYY-MM-DD-slug.md`.
2. Fill in the front matter, then paste the story below it. One blank line between paragraphs. No HTML needed.
3. Put any illustration in `assets/` and point `image:` at it.
4. Commit and push.

GitHub rebuilds the site. The new issue becomes the homepage and the previous one drops into `/archive/`. You never edit `index.html` or `archive.html`.

## Front matter

```yaml
---
title: "The Promise"
issue: "issue two"
kind: "Fiction"
minutes: 6
standfirst: "One line under the title. Write it last."
image: /assets/banyan.webp
image_alt: "Describe the picture for someone who cannot see it."
date: 2026-10-04
slug: the-promise
---
```

`image` and `image_alt` can both be left out; the figure disappears.

## Pictures: six ways to show them

Add a `picture:` line to the story's settings block. Leave it out and you get `left`.

| `picture:` | What it does | Best picture shape |
|---|---|---|
| `left` | Picture in the fixed left column, under the title (default) | Tall / portrait |
| `top` | Wide picture above the story | Wide / landscape |
| `middle` | Picture inside the story, after paragraph `picture_after` (default 5), with `caption` under it | Wide |
| `end` | Picture after the last line of the story, with `caption` under it | Wide |
| `panel` | Picture fills the whole left side; title sits on top of it | Tall, quiet top half |
| `strip` | Three square panels above the story, comic style | Three small drawings |

Examples:

```yaml
picture: middle
image: /assets/birds-wide.jpg
image_alt: "Describe the picture."
caption: "The birds kept coming down into the old tamarind."
picture_after: 9
```

```yaml
picture: strip
strip:
  - /assets/panel-1.jpg
  - /assets/panel-2.jpg
  - /assets/panel-3.jpg
```

No `image:` line (and not `strip`) means no picture; the left column shows only the title.

Image tips: lowercase file names with hyphens, no spaces; .jpg or .webp under 300 KB; upload with the final name, do not rename on GitHub (it can empty the file).

## Files

- `_config.yml` — site settings and the `/slug/` URL shape
- `_layouts/default.html` — the shell: head, fonts, all the CSS
- `_includes/issue.html` — one issue rendered; used by both the post page and the homepage
- `_layouts/issue.html` — wraps a post in the two above
- `index.html` — serves the newest post in full, no click, no redirect
- `archive.html` — lists every issue

## Before it goes live

The subscribe form posts to `#`. Change the `action` in `_includes/issue.html` to your Buttondown or Ghost endpoint.

## Running it locally (optional)

```
bundle install
bundle exec jekyll serve
```
