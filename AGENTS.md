# AGENTS.md

Guidance for AI coding agents working in this repository.

## What this is

Kevin Ren's academic personal website, hosted on GitHub Pages at
https://ren-kevin.github.io. It is a Jekyll site built on the
[academicpages](https://github.com/academicpages/academicpages.github.io)
template (a fork of Minimal Mistakes). GitHub Pages builds the `master` branch
automatically on push; there is no CI, test suite, or build step to run before
committing.

Most of the template's demo content is still present but unused. The live site
is small: a home page, a research page, a CV page, and a contact page.

## Layout

| Path | Purpose |
|---|---|
| `_config.yml` | Site-wide settings, author sidebar (name, bio, avatar, Google Scholar, LinkedIn). |
| `_data/navigation.yml` | Top nav: Research, CV, Contact. |
| `_data/links.yaml` | Paper link lists, keyed by a short slug (e.g. `kr_jmp`, `fpf_ban`). Each entry is a list of `{name, url}` buttons. |
| `_pages/about.md` | Home page (`permalink: /`). Bio blurb plus CV download button. |
| `_pages/research.md` | Research page. Sections: Job Market Paper, Refereed Publications, Working Papers, Work in Progress. |
| `_pages/cv.md` | CV page. Just a download button for `files/cv.pdf`. |
| `_pages/contact.md` | Address and email. |
| `_pages/old/` | Unused template pages, excluded from the build in `_config.yml`. Leave alone. |
| `_includes/paper_entry.html` | Custom include that renders one paper on the research page. See below. |
| `files/` | PDFs served at `/files/...`. `cv.pdf` is the live CV. Papers live under `files/working_papers/<slug>/` and `files/published_papers/`. |
| `images/IMG_6500_crop2.jpg` | Sidebar avatar. |
| `_sass/custom.scss` | Site-specific style overrides. `_sass/_buttons.scss` defines `.btn--generalbutton`, used for all paper/CV buttons. |
| `_publications/`, `_talks/`, `_teaching/`, `_portfolio/`, `_posts/`, `_drafts/` | Template demo content. Not linked from nav and not used on the live site. |
| `markdown_generator/`, `talkmap*` | Template tooling, unused. |
| `_site/` | Build output, gitignored. Never edit. |
| `dfasdfas` | Stray file containing an old diff. Harmless; ignore. |

## How papers are added or updated

A paper on the research page is two edits:

1. **Add the link list** to `_data/links.yaml` under a new slug:

   ```yaml
   my_paper:
     - name: "Paper"
       url: "https://ren-kevin.github.io/files/working_papers/my_paper/draft.pdf"
     - name: "SSRN Version"
       url: "https://papers.ssrn.com/..."
   ```

2. **Add an entry** to `_pages/research.md` in the right section:

   ```liquid
   {% include paper_entry.html
      title="Paper Title"
      coauthors="Coauthor One and Coauthor Two"
      status="Journal Name, 2026, 18(1): 44-87"
      links="my_paper" %}
   ```

   `coauthors`, `status`, and `links` are all optional. Omit `links` for work
   in progress with no PDF. `status` is rendered in italics and is used for
   publication venues or "Forthcoming at ...".

Paper PDFs go in `files/working_papers/<slug>/` (or `files/published_papers/`
for published versions). URLs in `links.yaml` are absolute and must match the
actual path on disk under `files/`. Double-check the path exists before
committing; a wrong URL silently 404s on the live site.

Updating the CV is just replacing `files/cv.pdf`. No other edit needed.

## Conventions

- **Minimal changes.** This is a content site maintained by one person. Do not
  refactor the theme, update dependencies, or remove unused template files
  unless asked.
- **Don't touch `_config.yml` casually.** It is the author profile and site
  identity. Changes there affect every page.
- **Keep the tone of the existing pages.** Short, plain, academic.
- **Commit messages** follow the existing style: short lowercase phrases
  describing the content change (e.g. `minor cv update`, `jmp revision`).
- Paper titles are rendered in the steel-blue bold style
  (`#4682B4`) by `paper_entry.html`. Don't inline styles in `research.md`.
- **Hide paper entries with `{% comment %} ... {% endcomment %}`, never an
  HTML comment.** Jekyll still executes `{% include %}` tags inside
  `<!-- -->`, and `paper_entry.html` begins with its own `-->`, which closes
  the outer comment early and leaks the entries onto the page. The Work in
  Progress section in `research.md` is hidden this way.

## Running locally

Ruby 3.2 and Bundler are installed on this machine. GitHub Pages pins
Jekyll 3.9 via the `github-pages` gem.

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. Always prefix with `bundle exec`; running
`jekyll` bare fails with a gem activation error. `_config.dev.yml` can be
layered in with `--config _config.yml,_config.dev.yml` to disable analytics
and use the localhost URL.

Local builds are optional. Most changes are markdown or YAML edits that are
safe to verify by reading.

## Deploying

Push to `master`. GitHub Pages rebuilds within a minute or two. There is no
separate `gh-pages` branch in use (the `staticman` config that mentions one is
leftover template config).
