---
name: planning
description: "Use when you have a validated idea and need a technical plan before touching code."
---

# Planning - Design & Implementation Plan

Take a validated idea and produce a technical plan.

## When to Use

- "How do we implement X?"
- "What files need to change for this feature?"
- "Plan the architecture for Y"

## Context

Read `docs/teamlet/context/stack.md` and `docs/teamlet/context/decisions.md` for tech constraints.
If files don't exist, proceed without them.

## Process

1. Scan relevant code structure first
2. Outline in chat:
   - Which files will be created or modified
   - Data flow (1-2 sentences)
   - Key risks or trade-offs
3. Get approval via `ask_user`:
   > choices: ["Looks good, start building", "Change the approach", "Need more detail", "Done for now"]
4. If user selects "Looks good" → recommend `build` as the next step

**If user says "quick":** Skip questions. If the change is under ~20 lines or a single file, recommend using `build` directly. Otherwise: outline in 2-3 sentences and ask whether to start building.

**If user says "thorough":** Write full plan to `docs/teamlet/plans/YYYY-MM-DD-<feature>.md`:
- Header: Goal, Architecture (3 sentences), Tech Stack
- Tasks: numbered, each with files to touch and what to do
- No full implementation code - describe intent
- No placeholders (TBD, TODO)

## Key Principles

- Match the stack - follow project context
- YAGNI - plan only what's needed
- Explore before designing - read existing code first
- No full code in plan files - describe what to build, not every line

## Example

User: "Plan the implementation for user authentication"

Your approach:
1. Scan existing code: check for auth-related files, middleware, user models
2. Outline:
   - Create: `src/middleware/auth.ts`, `src/models/user.ts`, `src/routes/auth.ts`
   - Modify: `src/app.ts` (add auth middleware), `package.json` (add bcrypt, jsonwebtoken)
   - Data flow: Login request → validate credentials → issue JWT → client stores token → middleware verifies on protected routes
   - Risks: Token refresh strategy (recommend short-lived access + refresh token)
3. Ask via ask_user: choices: ["Looks good, start building", "Change the approach", "Need more detail", "Done for now"]
