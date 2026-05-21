---
name: project-context
description: "Use when the user explicitly asks to create, read, remember, or update Teamlet project context memory."
---

# Project Context - Optional Project Memory

Persistent memory is useful only when it is explicit, short, and current.

## When to Use

Use only when the user explicitly asks to:
- Set up Teamlet memory or project context
- Remember project facts, tech stack, decisions, or constraints
- Update stale project context
- Read existing project memory for a task

Do not auto-trigger this skill. Missing context files are normal.

## Context Files

All files live in `docs/teamlet/context/` in the project repository.

| File | Default? | Purpose | Max size |
|---|---|---|---|
| `brief.md` | Yes | Product, audience, business model, stack, priority, avoid list | 40 lines |
| `stack.md` | Optional | Detailed tech stack, test/build commands, design system | 40 lines |
| `decisions.md` | Optional | Architecture/product decision log | 15 entries |

## Onboarding Process

When user asks to set up memory, ask one question at a time via `ask_user`:

1. "What are you building?" [freeform]
2. "Who is it for?" choices: ["B2C consumers", "B2B businesses", "Developers", "Internal tool"]
3. "What tech stack?" choices: ["Next.js", "React + Node", "Vue + Node", "React + .NET", "Other"]
4. "What phase?" choices: ["Exploring the idea", "Building MVP", "MVP live, growing", "Optimizing"]

Then create `docs/teamlet/context/brief.md`:

```markdown
# Teamlet Project Brief

Product: [name and one-liner]
Audience: [who and their pain]
Business model: [how it makes money, if known]
Phase: [current phase]
Stack: [short stack summary]
Design constraints: [brand/design system/accessibility constraints]
Current priority: [one immediate priority]
Avoid: [things the AI should not do]
```

After creating brief.md, offer optional files via `ask_user`:
> choices: ["Only brief.md", "Also create stack.md", "Also create stack.md and decisions.md"]

## Updating Context

- **brief.md** - replace relevant lines in place. Keep concise. Never append running history.
- **stack.md** - replace values, never append endlessly.
- **decisions.md** - format: `- [YYYY-MM-DD] Decision - brief rationale`. If >= 15 entries: summarize 5 oldest into one line, remove them, append new.

## Stale Context Rule

Repository evidence beats memory. If context says one thing and the code says another:
1. Follow the repository evidence for the current task
2. Tell the user the memory appears stale
3. Ask before updating memory

## Key Principles

- Opt-in only - never create memory automatically
- Bounded files - no unbounded progress logs
- Selective loading - load only what the task needs
- Repository evidence wins over stale memory
- No auto-commits - user controls version history

## Example

User: "Set up Teamlet memory for my project"

Your approach:
1. Ask: "What are you building?" [freeform]
2. User: "A habit tracking app for iOS and web"
3. Ask: "Who is it for?" choices: ["B2C consumers", "B2B businesses", "Developers", "Internal tool"]
4. User: "B2C consumers"
5. Ask: "What tech stack?" choices: ["Next.js", "React + Node", "Vue + Node", "React Native", "Other"]
6. User: "Next.js"
7. Ask: "What phase?" choices: ["Exploring the idea", "Building MVP", "MVP live, growing", "Optimizing"]
8. User: "Building MVP"
9. Create `docs/teamlet/context/brief.md` with the gathered info
10. Ask: "Want additional context files?" choices: ["Only brief.md", "Also create stack.md", "Also create both stack.md and decisions.md"]