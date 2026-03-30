---
title: Timeline
description: Complete timeline of how Anthropic's Claude session limits and peak hours have evolved since 2023.
---

# Timeline of Claude Session Limits

A chronological overview of how Anthropic has changed Claude's usage limits, session windows, and peak hours system.

## 2023

### Sep 2023 — Claude Pro launches

Anthropic introduced the **Claude Pro** plan at $20/month, initially in the US and UK. Usage limit: at least **100 messages per 8-hour period**, then reset. This was more generous than ChatGPT Plus at the time (50 messages per 3 hours).

Source: [SiliconANGLE](https://siliconangle.com/2023/09/07/anthropic-announces-claude-pro-paid-subscription-generative-ai-chatbot/)

## 2024

### Mid-2024 — Shift to 5-hour rolling window

Anthropic transitioned from the original 100 messages / 8 hours to a **5-hour rolling window** model. Pro subscribers could expect roughly **45 messages per 5 hours**, varying by conversation length and model. The exact date was not prominently announced.

### Dec 2024 — First public discussion of session limit changes

Early community discussion on Reddit about session limit frustrations, predating Claude Code's launch.

Source: [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1s4idaq/update_on_session_limits/)

## 2025

### Feb 2025 — Claude Code launches

Anthropic released **Claude Code** as a limited research preview — an agentic CLI tool for coding. Initially available to Pro subscribers only.

### Apr-May 2025 — Max plan introduced

Anthropic launched the **Max plan** with two tiers:

| Plan | Price | Usage |
|---|---|---|
| Max 5x | $100/month | 5x Pro usage |
| Max 20x | $200/month | 20x Pro usage |

Both tiers included priority access to newest features and models.

Source: [Anthropic](https://www.anthropic.com/news/max-plan)

### May 2025 — Claude Code reaches general availability

Claude Code became available to all users including free tier. Demand began growing rapidly.

### Jul 28, 2025 — Weekly rate limits announced

Anthropic announced **new weekly rate limits** on top of the existing 5-hour session limits, targeted at heavy Claude Code users. Effective date: August 28, 2025. Estimated to affect fewer than 5% of subscribers.

Expected weekly allowances:

| Plan | Sonnet 4 / week | Opus 4 / week |
|---|---|---|
| Pro | 40-80 hours | — |
| Max 5x | 140-280 hours | 15-35 hours |
| Max 20x | 240-480 hours | 24-40 hours |

Max subscribers gained the ability to purchase additional usage at API rates.

Source: [TechCrunch](https://techcrunch.com/2025/07/28/anthropic-unveils-new-rate-limits-to-curb-claude-code-power-users/)

### Aug 28, 2025 — Weekly rate limits go into effect

The dual-layer system became active: **5-hour rolling session window** plus a **7-day weekly ceiling**.

Source: [Portkey](https://portkey.ai/blog/claude-code-limits/)

### Sep 2025 — Sonnet 4.5 triggers usage limit crisis

Claude Sonnet 4.5 released. Users immediately reported dramatically reduced effective usage:

- **Before:** Pro users expected 40-80 hours/week
- **After:** Users reported only **6-8 hours/week** — an ~85% reduction
- 30+ bug reports filed on GitHub ([Issue #9094](https://github.com/anthropics/claude-code/issues/9094)), 121 comments
- Users on Max 20x exhausting limits in 3 days
- Some users consuming 27% of their 5-hour limit with just 2 requests

### Oct 2025 — Megathread and widespread complaints

r/ClaudeAI created a dedicated megathread for usage limit complaints. Widespread reports of Pro, Max 5x, and Max 20x plans being unusable. Users reported cancellations and downgrades.

### Dec 25-31, 2025 — Holiday 2x usage promotion

Anthropic **doubled** both 5-hour session limits and weekly caps for Pro and Max subscribers. Applied to Claude web app, Claude Code, and Claude in Chrome. No additional charge.

Source: [Claude Help Center](https://support.claude.com/en/articles/13163666-holiday-2025-usage-promotion)

## 2026

### Jan 2026 — Post-holiday limit complaints

After the holiday promotion expired, developers reported sharply reduced capacity. Some claimed ~60% reduction vs. pre-holiday baseline. Max subscribers hitting limits in 10-15 minutes. Anthropic attributed it to normal return to standard limits.

Source: [The Register](https://www.theregister.com/2026/01/05/claude_devs_usage_limits/)

### Early 2026 — Opus-specific caps removed

For Claude and Claude Code users with Opus 4.5 access, Anthropic removed Opus-specific caps. Max and Team Premium users received increased overall limits so Opus token allowance roughly matched previous Sonnet levels.

Source: [Anthropic](https://www.anthropic.com/news/claude-opus-4-5)

### Mar 13-28, 2026 — Off-peak 2x usage promotion

Anthropic **doubled** usage limits during off-peak hours for two weeks. Eligible for Free, Pro, Max, and Team plans (not Enterprise). Extra usage did not count toward weekly limits.

Source: [Claude Help Center](https://support.claude.com/en/articles/14063676-claude-march-2026-usage-promotion)

### Mar 23-26, 2026 — Peak hours system introduced

Users began noticing rapid limit depletion around March 23 (usage meters jumping from 52% to 91% in minutes). Anthropic remained silent for several days.

On **March 26**, Anthropic engineer Thariq Shihipar confirmed via X/Twitter and Reddit that Anthropic was **adjusting 5-hour session limits during peak hours**:

- **Peak hours:** Weekdays 5:00-11:00 AM PT / 1:00-7:00 PM GMT
- During peak, token cost per session is higher — the 5-hour allowance depletes faster
- During off-peak, users get more out of their session
- **Weekly limits unchanged** — only intra-week distribution changed
- ~**7% of users** affected, particularly Pro tier
- Max 20x users largely insulated (~2% seeing differences)

Sources: [The Register](https://www.theregister.com/2026/03/26/anthropic_tweaks_usage_limits/), [gHacks](https://www.ghacks.net/2026/03/27/anthropic-reduces-claude-session-limits-during-peak-hours-for-free-pro-and-max-users/), [TechRadar](https://www.techradar.com/ai-platforms-assistants/claude/claude-is-limiting-usage-more-aggressively-during-peak-hours-heres-what-changed), [MacRumors](https://www.macrumors.com/2026/03/26/claude-code-users-rapid-rate-limit-drain-bug/)

## Summary

The limit system has evolved through several phases:

| Period | System |
|---|---|
| Sep 2023 | 100 messages / 8 hours |
| Mid-2024 | ~45 messages / 5-hour rolling window |
| Aug 2025 | 5-hour sessions + 7-day weekly ceiling |
| Sep 2025 | Effective limits drop sharply with Sonnet 4.5 |
| Mar 2026 | Peak/off-peak pricing within 5-hour sessions |

The overall trend: as Claude's capabilities and user base grew, Anthropic progressively added more layers to manage demand — from simple message counts to time-based sessions to weekly caps to peak-hour multipliers.
