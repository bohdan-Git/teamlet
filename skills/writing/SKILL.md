---
name: writing
description: "Use for any text content: landing page copy, UI microcopy, email templates, translations, README, API docs, changelogs, user guides. Writes in the project tone of voice."
---

# Writing - Copy, Docs & Translations

All text output in one skill. Every word serves the business goal.

## When to Use

- Landing page copy, marketing text
- UI microcopy (buttons, errors, empty states, tooltips)
- Email templates
- Translations and i18n
- README, API docs, changelogs, user guides

## Context

Read `docs/teamlet/context/brief.md` for product, audience, and tone info.
If the file doesn't exist, proceed without it.

## Process

1. Identify content type (if unclear, ask via `ask_user` with choices: ["Landing page / marketing copy", "UI microcopy", "Documentation", "Translation / i18n", "Email template"])
2. Derive tone from existing copy. If no tone is established, ask once via `ask_user`: choices: ["Professional", "Friendly-casual", "Bold-playful", "Technical-precise"]
3. Draft one polished version with rationale
4. Present for feedback

**If user says "quick":** Draft immediately, no questions. One polished version.
**If user says "thorough":** Research existing copy + competitors, present 2-3 strategic variants with rationale, iterative refinement.

## Writing Templates

**Error message:** "[What failed]. [How to fix]. [Action button]"
→ "Payment declined. Check your card details and try again. [Retry payment]"

**Empty state:** "[Explain what goes here] + [encourage action]"
→ "No projects yet. Create your first one to get started. [Create project]"

**Hero headline:** "[Specific benefit] + [for whom]"
→ "Ship 2x faster - AI dev tools for solo founders"

**CTA button:** "[Action verb] + [outcome]"
→ "Start free trial" / "Save draft" / "Create account"

**Confirm dialog:** "[Restate action] + [consequence]"
→ "Delete this project? All files and history will be permanently removed."

## Documentation Rules

1. **Code is truth** - inspect actual code before documenting behavior
2. **Verify examples run** - code examples must be tested or copied from working code
3. **Update on change** - when code changes, flag affected docs
4. **No aspirational docs** - document what exists today, not what's planned

Formats:
- README: Title, one-liner, install, usage, env vars, contributing
- API docs: endpoint, method, params, response shape, errors, example curl
- Changelog: `## [version] - YYYY-MM-DD` → Added / Changed / Fixed / Removed

## Translations & i18n

- Translate meaning, not words literally
- Output in exact format the codebase uses (i18next keys, vue-i18n, etc.)
- Flag culturally sensitive content for human review

## Writing Principles

- **Clear > Clever** - wordplay fails in translation
- **Short > Long** - every word earns its place
- **Specific > Vague** - numbers beat adjectives
- **Benefit > Feature** - "Get paid faster" beats "Stripe integration"
- **Active voice** - always
- **No dark patterns** - no fake urgency, no misleading copy

## Self-Review Before Presenting

- Does every sentence serve a purpose?
- Is the CTA clear and specific?
- Would the target audience understand this?
- Is tone consistent with existing copy?

## Example

User: "Write error messages for our payment form"

Your approach:
1. Content type: UI microcopy (clear from request)
2. Tone: derive from existing copy, or ask if no reference exists
3. Draft using error template "[What failed]. [How to fix]. [Action]":
   - Card declined: "Your card was declined. Try a different payment method. [Use another card]"
   - Expired card: "This card has expired. Update your card details to continue. [Update card]"
   - Network error: "Connection lost. Check your internet and try again. [Retry payment]"
4. Present all messages together for feedback
