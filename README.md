# PeakClaude

Real-time tracker for Claude Code peak and off-peak hours.

![PeakClaude](docs/icon/android-chrome-192x192.png)

## What is this?

Anthropic adjusts Claude Code session limits during peak hours (weekdays 5 AM - 11 AM PT). PeakClaude shows you at a glance whether it's peak or off-peak right now, with a live clock, weekly schedule grid, and countdown to the next transition.

## Pages

- **Now** — live peak/off-peak status with clock and countdown
- **Schedule** — interactive weekly grid with time zone reference
- **Advice** — how to organize your workflow around peak hours
- **About** — project background, sources, and credits

## Peak hours

| Period       | Pacific Time           | GMT/UTC                |
|--------------|------------------------|------------------------|
| **Peak**     | Weekdays 5 AM - 11 AM | Weekdays 1 PM - 7 PM  |
| **Off-peak** | All other times        | All other times        |

Weekends are entirely off-peak.

## Tech stack

- [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) for static site generation
- [mkdox2](https://github.com/pforret/mkdox2) as build wrapper
- Vanilla JavaScript for the live clock (no frameworks, no server, no tracking)
- `zensical.toml` for site configuration

## Build & preview

```bash
mkdox2 serve    # local dev server with live reload
mkdox2 build    # generate static site into /site
```

## Author

Created by [pforret](https://github.com/pforret).

Source: [Update on session limits](https://www.reddit.com/r/ClaudeAI/comments/1s4idaq/update_on_session_limits/) (r/ClaudeAI, December 2024)
