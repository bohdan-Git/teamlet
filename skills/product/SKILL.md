---
name: product
description: "Use when deciding what to build next, exploring a new idea, or analyzing competitors. Covers discovery (what to build) and ideation (how to approach it). One question at a time via ask_user."
---

# Product - Discovery & Ideation

Two jobs: **What to build?** (discovery) and **How to approach it?** (ideation).

## When to Use

- "What should I build next?"
- "Let's add X feature"
- "What are competitors doing?"
- "Should I build this or buy it?"

## Context

Read `docs/teamlet/context/brief.md` for product, audience, and phase info.
If the file doesn't exist, proceed without it.

## Process

1. Ask up to 3 questions one at a time via `ask_user` (multiple choice preferred)
2. Score Impact/Effort (1-5): revenue impact, user retention, dev time, complexity
3. Propose 2-3 approaches with trade-offs, mark your recommendation
4. Include MVP slice (see below) in your recommendation
5. Get approval via `ask_user`

**If user says "quick":** 1 question max, give direct recommendation, done.
**If user says "thorough":** Add competitive scan (2-3 competitors) + write spec to `docs/teamlet/specs/YYYY-MM-DD-<topic>.md`.

## MVP Slice (Required in Every Recommendation)

1. **Core user action** - the one thing users must be able to do
2. **Cut list** - features explicitly deferred ("not in MVP: X, Y, Z")
3. **Success signal** - one measurable indicator it worked
4. **Time box** - max build time before shipping

If the idea is too large for one MVP slice, break into sequential slices and recommend which to ship first.

## Question Guidelines

- One question at a time via `ask_user` tool
- Multiple choice preferred over freeform
- Business before technical - why before how
- YAGNI - push back on unnecessary scope
- Skip what context already answers

## Transition

After approval, ask:
> "Ready to move to planning?"
> choices: ["Yes, create the plan", "I want to adjust something first", "Done for now"]

## Example

User: "I'm thinking about adding a referral program"

Your approach:
1. Read brief.md for phase/audience (proceed without if missing)
2. Ask via ask_user: "What's the main goal?" choices: ["More signups", "Reduce acquisition cost", "Increase engagement", "Revenue growth"]
3. Score Impact/Effort based on answer + context
4. Present recommendation:
   - **Recommendation:** Simple invite-link referral with signup bonus
   - **MVP slice:**
     - Core action: Existing user shares link → new user gets bonus on signup
     - Cut: No dashboard, no tiers, no gamification, no leaderboard
     - Success signal: 10 referred signups in first week
     - Time box: 2 days dev
   - **Trade-offs:** Simple but no viral loop; can add tiers later
5. Ask: "Ready to plan?" choices: ["Yes, create the plan", "Adjust something", "Done"]
