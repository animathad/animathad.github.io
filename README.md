# animathad.github.io

The source for my personal site — [animathad.github.io](https://animathad.github.io).
A blog, a digital garden of notes, and an about page. Built with [Jekyll](https://jekyllrb.com/)
and deployed to GitHub Pages via GitHub Actions.

## Writing

- **Blog posts** live in `_posts/` as `YYYY-MM-DD-title.md`. Front matter:

  ```yaml
  ---
  title: My post title
  tags: [ai, platforms]
  description: One line for search/social previews.
  ---
  ```

- **Garden notes** live in `_notes/Public/` as `Title.md`. Front matter:

  ```yaml
  ---
  title: My note
  feed: show        # "show" lists it in the garden; "hide" keeps it unlisted
  date: 2026-07-30  # ISO date
  ---
  ```

  Notes support wiki-style links — `[[Another Note]]` — with automatic backlinks
  and hover previews.

## Editing the site

- Identity, links, and settings: `_config.yml` (restart the server after changes).
- Design system: `assets/css/portfolio.css` (colours, fonts, components).
- Home page: `_includes/Homepage.html` · Nav: `_includes/Nav.html` · Footer: `_includes/Footer.html`.
- About page: `pages/about.md`.
- Swap the placeholder monogram (`assets/img/profile.svg`) for a real photo any time.

## Running locally

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000>. Pushing to `main` triggers the GitHub Actions
workflow in `.github/workflows/pages.yml`, which builds and deploys automatically.

## Credits

Built on the open-source [Jekyll Garden](https://github.com/Jekyll-Garden/jekyll-garden.github.io)
theme (MIT) by Raghuveer S, Hiran Venugopalan, and Asim K T — reworked and restyled.
Dark-mode switcher adapted from [Derek Kedziora](https://github.com/derekkedziora).
See [/colophon](https://animathad.github.io/colophon) for the full rundown.

Licensed under the [MIT License](LICENSE).
