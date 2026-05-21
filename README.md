# Teamlet

AI-powered skill set that replaces a startup team: PM, designer, copywriter, SEO specialist, and developer - all in your editor.

Built for solo web founders. Works with GitHub Copilot, Claude Code, and Codex. Optimized for Claude Sonnet/Haiku, Qwen 35B, Gemma 4, and similar models.

## Quick Start

1. **Just describe your task.** Teamlet routes to the right skill automatically via keyword matching.
2. **Answer the menu choices.** Skills ask focused questions via multiple-choice (not open-ended).
3. **Get the output.** Code, copy, plans, audits - verified and ready to use.

No setup required. Project memory is optional - ask "set up Teamlet memory" if you want persistent context.

## Skills

| Skill | Use when... | Example prompts |
|---|---|---|
| `product` | Deciding what to build next | "What should I build next?" / "Prioritize my backlog" |
| `planning` | You need a technical plan before code | "Plan the auth architecture" / "What files need to change?" |
| `build` | Writing code or fixing bugs | "Implement this component" / "Fix the login bug" |
| `ui-ux-design` | Designing UI, components, accessibility | "Design the pricing page" / "Check accessibility" |
| `writing` | Any text: marketing, docs, translations | "Write landing page copy" / "Translate to German" |
| `seo-optimization` | SEO audits, meta tags, Core Web Vitals | "Audit SEO for homepage" / "Add Open Graph tags" |
| `analytics-growth` | Metrics, funnels, event tracking | "What metrics should I track?" / "Set up conversion tracking" |
| `launch-readiness` | Pre-ship checklist | "Am I ready to launch?" / "What am I forgetting?" |
| `project-context` | Save/update project memory | "Remember we switched to Next.js" |

## Depth Override

Every skill has one default process. You can override with explicit words:

| Override | Effect |
|---|---|
| **"quick"** / "just do it" | Skip all questions, act directly, minimal output |
| **"thorough"** / "full process" | Extended steps, written files, more questions |
| *(nothing said)* | Default process - a few targeted questions, then execute |

## How It Works

```
You → describe task
     ↓
using-teamlet → matches keywords to skill
     ↓
Skill → asks only necessary questions (multiple choice)
     ↓
Output → verified result (code, copy, plan, audit)
     ↓
Transition → asks before moving to next skill (never auto-chains)
```

## Project Memory (Optional)

Ask "set up Teamlet memory" to create `docs/teamlet/context/brief.md` - a short file (~40 lines) with your product, audience, stack, and priorities.

Skills load it automatically when relevant. No setup = no problem - everything works without it.

| File | Purpose |
|---|---|
| `brief.md` | Product, audience, business model, stack, current priority |
| `stack.md` | Optional: detailed tech stack, test/build commands |
| `decisions.md` | Optional: architecture decision log (rolling 15 entries) |

## Token-Saving Tips

- Say **"quick"** for simple tasks - skips all intermediate steps
- Go directly to the right skill: translation → `writing`, small UI fix → `ui-ux-design`
- Don't start with `product` for tasks where you already know what to build
- Use `/compact` in long sessions

## Safety Guarantees

- **No auto-chaining** - skills never call each other without your confirmation
- **No hallucinated completion** - `build` always runs verification before claiming "done"
- **No runaway loops** - max 2 retries on any failing tool, then reports the blocker
- **No subagent hangs** - 4 anti-stuck rules prevent common subagent failure modes

## Installation

**GitHub Copilot:** Copy this repo into your project. The `.github/copilot-instructions.md` file is auto-loaded.

**Claude Code / Codex:** Copy this repo into your project. The `CLAUDE.md` file is auto-loaded.

Skills live in the `skills/` folder and are discovered automatically by the platform.
