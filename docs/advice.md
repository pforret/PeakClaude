---
title: Practical Advice
description: Practical advice for organizing your Claude Code workflow around peak and off-peak hours to maximize productivity.
---

# Advice for Working Around Peak Hours

Peak hours mean tighter session limits, not less total capacity. With a bit of planning, you can get the same amount of work done without hitting walls.

## Plan your day around the schedule

| Time window | Status | Best use |
|---|---|---|
| Weekdays before 5 AM PT | Off-peak | Heavy refactors, batch operations |
| Weekdays 5 AM - 11 AM PT | **Peak** | Light tasks, reviews, planning |
| Weekdays after 11 AM PT | Off-peak | Resume intensive work |
| Weekends (all day) | Off-peak | No restrictions |

## Shift heavy work to off-peak

Token-intensive tasks burn through your session limits fast during peak. Move them to off-peak windows:

- **Large refactors** spanning many files
- **Code generation** for new features or boilerplate
- **Background agents** running autonomously
- **Batch operations** like bulk file processing or migrations

> *"If you run token-intensive background jobs, shifting them to off-peak hours will stretch your session limits further."*

## Reduce token usage during peak

When you do work during peak hours, make every token count:

- **Keep prompts focused.** Ask one thing at a time instead of multi-part requests.
- **Use `/compact`** to compress conversation context when it grows large.
- **Disable unused plugins.** Each active MCP server or skill adds to context size.
- **Don't dump entire files.** Point Claude to specific lines or functions instead of pasting whole files.
- **Start fresh sessions.** A clean conversation uses fewer tokens than continuing a long one.

## Use peak hours for low-token tasks

Some work barely touches your limits. Save these for peak hours:

- **Code review** — reading diffs, spotting issues
- **Planning** — designing architecture, writing specs
- **Quick questions** — short Q&A about APIs or syntax
- **Documentation** — writing or editing docs
- **Manual work** — tasks you do yourself with Claude on standby

## Spread work across tools

Diversifying across AI tools means no single one bottlenecks you:

- **Google Gemini** — strong for code and general tasks
- **OpenAI ChatGPT / Codex** — alternative coding assistant
- **Local models** (Ollama, LM Studio) — unlimited, no rate limits
- **GitHub Copilot** — inline completions don't count against Claude limits

Use Claude for what it does best and fall back to alternatives when you're near your limit.

## Weekly rhythm

Your weekly token budget doesn't change — only how it's distributed. Think of it like electricity pricing: same total supply, cheaper at off-peak times.

- **Monday-Friday mornings (PT):** conserve, do lightweight work
- **Afternoons and evenings:** go heavy, no restrictions
- **Weekends:** full capacity, great for deep work sessions

The [weekly schedule](schedule.md) page shows exactly where you are right now.
