---
name: using-teamlet
description: "Routes requests to the right Teamlet skill."
---

<SUBAGENT-STOP>
If you were dispatched as a subagent to execute a specific task, skip this skill entirely.
</SUBAGENT-STOP>

## Skill Triggers (match FIRST that fits)

1. User mentions "SEO", "meta tags", "sitemap", "robots.txt", "structured data", "Core Web Vitals" → `seo-optimization`
2. User mentions "launch", "ready to ship", "pre-launch", "checklist", "ready to deploy" → `launch-readiness`
3. User mentions "metrics", "tracking", "analytics", "funnel", "retention", "pricing experiment" → `analytics-growth`
4. User mentions "remember", "save context", "update memory", "project context", "set up memory" → `project-context`
5. User asks what to build, prioritize, competitive analysis, or feature ideas → `product`
6. User asks to plan, architect, or design a system → `planning`
7. User asks to write code, fix bugs, or implement features → `build`
8. User asks about UI design, components, styles, accessibility, or redesign → `ui-ux-design`
9. User asks for text content: copy, docs, email, translation, README → `writing`
10. None match clearly → answer directly without invoking a skill

Simple factual question or tiny request → answer directly, no skill needed.

## Depth Override

Every skill has one default process. User can override depth:

- User says "quick", "just do it", or "no questions" → skip questions, act directly, minimal output
- User says "thorough", "full process", or "deep dive" → extended steps, written files, more questions

If neither is said, use the default process.

## Skill Transitions

Never auto-chain skills. Each transition requires explicit user confirmation:
```
product → (ask_user) → planning → (ask_user) → build
```

## ask_user Policy

Use the `ask_user` tool (not plain text) when:
- 2+ reasonable directions exist and the choice changes the outcome
- Info cannot be inferred from code or context
- Transitioning to next skill

## Project Memory

Opt-in only. Do not check for `docs/teamlet/context/` on first interaction.
- User asks to set up/remember/update context → invoke `project-context`
- Context files exist → skills load only what they need
- Repository evidence beats stale memory; ask before updating
