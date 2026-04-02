# ClearDataLabs

AI, neural networks, and browser demos — explained from scratch.

**Live site:** [cleardatalabs.com](https://cleardatalabs.com)

## Local development

```bash
bundle install
bundle exec jekyll serve --livereload
```

The site serves at `http://localhost:4000`. Requires Ruby and Bundler.

## Structure

```
_layouts/       Page templates (default, page, post)
_includes/      Partials (head, header, footer)
_posts/         Blog articles (YYYY-MM-DD-slug.md)
assets/css/     Single stylesheet
assets/img/     Images
```

Content is written in Markdown. New articles go in `_posts/` with date-prefixed filenames and Jekyll front matter.

## License

MIT — [Kostiantyn Chumychkin](https://github.com/kchumichkin)
