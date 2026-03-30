---
description: What is PeakClaude, why it exists, and how Claude Code peak hours work.
---

# About PeakClaude

PeakClaude is a simple real-time tracker that shows whether **Claude Code** is currently in peak or off-peak hours.

## Why does this exist?

In early 2025, Anthropic introduced **peak hours** for Claude Code to manage growing demand. During peak hours, 5-hour session limits are distributed more tightly, which can affect heavy users — especially on the Pro tier.

The schedule is straightforward but easy to forget, particularly across time zones. PeakClaude gives you a glanceable answer: **peak or not?**

## How peak hours work

| Period       | When (Pacific Time)        | When (GMT/UTC)             |
|--------------|----------------------------|----------------------------|
| **Peak**     | Weekdays 5:00 AM - 11:00 AM | Weekdays 1:00 PM - 7:00 PM |
| **Off-peak** | All other times            | All other times            |

- Weekends are entirely off-peak.
- Weekly token limits stay the same — only the per-session distribution changes.
- About 7% of users are affected, mostly those running token-intensive workflows during peak windows.

## Tips for working with peak hours

- **Schedule heavy jobs off-peak.** Background tasks, large refactors, and batch operations are best run outside the peak window.
- **Use weekends.** Saturday and Sunday have no peak restrictions at all.
- **Monitor your usage.** If you're hitting session limits, check whether you're consistently working during peak hours.

## How it works

PeakClaude runs entirely in the browser. It uses JavaScript's `Intl.DateTimeFormat` with the `America/Los_Angeles` timezone to determine the current Pacific Time, then compares it against the known peak schedule. No server, no API calls, no tracking.

## Source

Peak hours were announced by Anthropic in December 2024:
[Update on session limits](https://www.reddit.com/r/ClaudeAI/comments/1s4idaq/update_on_session_limits/) (r/ClaudeAI)

## Built by

Created by [pforret](https://github.com/pforret) using [MkDocs Material](https://squidfunk.github.io/mkdocs-material/). Source code on [GitHub](https://github.com/pforret/PeakClaude).
