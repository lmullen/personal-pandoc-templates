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

The standard Pandoc default LaTeX template with two localized customization blocks:

1. **IBM Plex font support** (marked with `% Customizations` comment): Activated by setting `plex: true` in YAML. Loads `plex-otf` with tuned scaling. Optionally set `sans: true` to use Plex Sans as the default family.
2. **Compact title block**: Title, subtitle, author, and date use reduced `\vspace` and `\normalsize` to produce a tighter header.

When merging upstream changes, these two blocks are the only areas that will conflict.

## Support files

- `mason-letterhead.pdf` — GMU letterhead background image
- `mullen-signature.pdf` — digital signature

Both are referenced from `~/.pandoc/templates/` in the letter template.

## Current state

The fork is behind upstream (last synced around Pandoc 2.7.3; upstream is at 3.9+). Merge conflict artifacts (`default.latex.orig`, `default.latex.rej`) from a previous sync attempt are still in the repo and can be cleaned up.
