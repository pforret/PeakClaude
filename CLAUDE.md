# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

PeakClaude is a Zensical documentation website built with MkDocs Material. The homepage will contain a real-time clock indicating whether the current time falls within Claude Code peak hours (weekdays 5am-11am PT / 1pm-7pm GMT).

## Build & Preview Commands

- `mkdox2 serve` — local dev server with live reload
- `mkdox2 build` — generate static site into `/site`

The `mkdox2` tool is a bash wrapper (installed via basher) that manages MkDocs Material sites.

## Architecture

- **`zensical.toml`** — project config (replaces `mkdocs.yml`). Defines site metadata, theme settings, markdown extensions, and plugins. The `mkdox2` tool reads this TOML and generates the MkDocs config.
- **`docs/`** — all source content (Markdown files, icons, overrides)
- **`docs/overrides/`** — MkDocs Material theme overrides (custom templates, analytics)
- **`docs/about/index.pre` + `index.post`** — pre/post fragments assembled by `mkdox2` into `index.md`
- **`site/`** — generated output

## Theme & Styling

- MkDocs Material with `red` primary palette, Nunito font
- Custom overrides in `docs/overrides/` (extends `base.html`)
- Enabled extensions: admonitions, code copy, tabbed content, task lists, mermaid diagrams, emoji, superfences

## Key Constraints

- Content is Markdown in `docs/` — edit `.md` files, not generated HTML
- The `about/index.md` is generated from `.pre` and `.post` fragments — edit those instead
- The peak hours clock feature needs to be added to the homepage (`docs/index.md` or via overrides)
