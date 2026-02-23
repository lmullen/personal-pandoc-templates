# Personal Pandoc Templates

## Purpose

This repository is a fork of [jgm/pandoc-templates](https://github.com/jgm/pandoc-templates), the official default templates for Pandoc. It serves two purposes:

1. **Track upstream**: Keep the default Pandoc templates up to date with new releases.
2. **Custom templates**: Maintain personal LaTeX templates for letters and academic papers.

## Git remotes

- `origin`: `https://github.com/lmullen/personal-pandoc-templates.git`
- `upstream`: `https://github.com/jgm/pandoc-templates.git`

To sync with upstream: `git fetch upstream && git merge upstream/master`. Resolve any conflicts in `default.latex` carefully, preserving the customization blocks described below.

## Custom templates

### `letter-mason.latex`

Letter template for GMU (Mason) letterhead. Uses the `wallpaper` package to overlay `mason-letterhead.pdf` as the header. Set in IBM Plex Serif. Includes a digital signature image (`mullen-signature.pdf`) in the closing block unless a `signature` YAML variable overrides it.

Key YAML variables: `address`, `salutation`, `closing`, `signature`, `date`, `linestretch`.

### `default.latex`

As of Pandoc 3.9, the default LaTeX template is modular: `default.latex` includes partials (`fonts.latex`, `font-settings.latex`, `common.latex`, `hypersetup.latex`, `passoptions.latex`, `document-metadata.latex`, `after-header-includes.latex`) via Pandoc's `$file.latex()$` syntax.

Two localized customization blocks in `default.latex`:

1. **IBM Plex font support** (marked with `% Customizations` comment, between `header-includes` and `after-header-includes.latex()`): Activated by setting `plex: true` in YAML. Loads `plex-otf` with tuned scaling. Optionally set `sans: true` to use Plex Sans as the default family.
2. **Compact title block**: Title, subtitle, author, and date use reduced `\vspace` and `\normalsize` to produce a tighter header.

When merging upstream changes, these two blocks are the only areas in `default.latex` that will conflict.

## Support files

- `mason-letterhead.pdf` — GMU letterhead background image
- `mullen-signature.pdf` — digital signature

Both are referenced from `~/.pandoc/templates/` in the letter template.

## Current state

Synced to upstream tag 3.9 (Pandoc 3.9).

## Maintenance

Periodically check for new upstream releases: `git fetch upstream --tags && git tag -l --sort=-version:refname | head -5`. Use `/sync-upstream` to merge a new tag while preserving local customizations.
