# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Install dependencies (first time or after Gemfile changes)
bundle install

# Serve locally with live reload
bundle exec jekyll serve

# Build static site into _site/
bundle exec jekyll build
```

> **Note:** `_config.yml` changes require a server restart — live reload does not pick them up automatically.

## Architecture

This is a **Jekyll** static site using the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) remote theme (`mmistakes/minimal-mistakes`). The site is deployed via GitHub Pages.

### Key files and directories

| Path | Purpose |
|------|---------|
| `_config.yml` | Site-wide settings: author profile, sidebar links, plugins, theme skin, permalink structure |
| `index.html` | Home page (uses `layout: home` from the theme) |
| `_pages/` | Static pages (About, Publications, archive pages) — included via `include: _pages` in config |
| `_posts/` | Blog posts in Markdown, named `YYYY-MM-DD-title.md` |
| `_data/navigation.yml` | Top navigation bar links |
| `assets/css/main.css` | Custom CSS layered on top of the theme |
| `assets/images/` | Images referenced in posts and pages |
| `assets/files/` | Downloadable files (e.g., `resume_full.pdf`) |

### Content conventions

**Publications page** (`_pages/publications.md`): Uses custom HTML with CSS classes rather than Markdown. The structure is `.pub-year-row > (.pub-list + .pub-year)`, where each `.pub-entry` contains `.pub-title`, `.pub-authors`, `.pub-venue`, and `.pub-btn` links. Use `<span class="pub-me">` to highlight the site author's name.

**Blog posts**: Use front matter with `title`, `categories` (usually `Blog`). Images go in `assets/images/` and are referenced with relative paths like `../../assets/images/filename.jpg`. Use `.image-wrapper` for single centered images and `.image-row` with nested `.image-wrapper` divs for side-by-side image grids.

**Custom CSS** (`assets/css/main.css`): This file extends the Minimal Mistakes theme. Custom component classes defined here: `.pub-*` (publications layout), `.image-wrapper` / `.image-row` (blog post image layouts). The site uses the `dark` skin.

**Navigation** (`_data/navigation.yml`): Edit the `main:` list to add/remove top nav links. Current nav: Blogs, Publications, About.
