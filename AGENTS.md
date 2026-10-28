# Repository Guidelines

## Project Structure & Module Organization

This repository contains a single-page Jekyll academic homepage deployed through GitHub Pages. There is no JavaScript framework or theme plugin.

- `index.html` selects `_layouts/home.html`, the only page template.
- `_data/profile.yml` is the single entry point for personal content, contact links, publications, experience, education, awards, and section order.
- `assets/css/home.css` defines styling and responsive layouts. The Chinese name uses system Kai fonts. `assets/favicon.svg` supplies the favicon.
- `chuliyun.jpg` and `resume.pdf` are the profile photo and downloadable CV. `_config.yml` contains deployment settings.

## Build, Test, and Development Commands

Run commands from the repository root:

- `bundle install`: install the Ruby dependencies listed in `Gemfile`.
- `bundle exec jekyll serve --livereload --host 127.0.0.1`: preview at `http://127.0.0.1:4000`.
- `bundle exec jekyll build --safe`: build the static site in `_site/` using GitHub Pages-compatible safe mode.

Restart the preview after changing `_config.yml`. Node.js, npm, and Docker are unnecessary.

## Coding Style & Naming Conventions

Use two spaces for YAML, HTML, and CSS blocks; match surrounding formatting. Keep new content in `profile.yml`. Preserve unique, lowercase, hyphenated section IDs because navigation uses them as anchors. Use `visible: false` to hide sections or entries.

Keep the page usable without JavaScript. Use Jekyll URL filters for local links and relative URLs for CSS assets. Keep Chinese-name font rules in `.name-chinese-text` so the halfwidth parentheses retain Latin typography.

## Testing Guidelines

No automated test framework, coverage threshold, formatter, or linter is configured. Build before committing. Check rendered content, navigation anchors, local asset paths, and mobile layout after relevant changes. Ensure build output excludes source data, documentation, dependencies, and caches.

## Commit & Pull Request Guidelines

Use short, descriptive commit subjects and follow any message explicitly requested by the user. Keep changes focused. Describe the resulting behavior and validation in pull requests; include screenshots for visual changes. Do not commit `_site/`, installed dependencies, or local tooling settings.
