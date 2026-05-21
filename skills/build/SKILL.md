---
name: build
description: "Use when implementing code or fixing bugs. Writes, verifies, and reports with evidence. Subagents communicate via output text, never via ask_user."
---

# Build - Implement & Verify

Write code, verify it works, report with evidence. No completion claims without proof.

## When to Use

- "Implement X"
- "Fix this bug"
- "Make the tests pass"
- Executing a plan from the `planning` skill

## Context

Read `docs/teamlet/context/brief.md` and `docs/teamlet/context/stack.md` for stack and build commands.
If files don't exist, proceed without them.

## Process

1. **Read** - scan relevant files before touching anything
2. **Implement** - follow existing patterns, minimal scope (YAGNI)
3. **Verify** - run the appropriate command (see verification table)
4. **Report** - summary + verification evidence

**If user says "quick":** Implement directly, run verification, report with evidence.
**If user says "thorough":** Break into phases. Implement with checkpoints - ask approval between phases.

## Verification

| Task type | Verification |
|---|---|
| Bug fix | Reproduce → fix → confirm symptom gone |
| New feature | Run test suite → new tests pass |
| Refactor | Full test suite → 0 regressions |
| UI change | Build succeeds |
| API change | Run tests or curl the endpoint |

**Iron Law:** No completion claims without fresh verification evidence. Run the command. Read the output. THEN report.

## Code Quality

Before reporting done:
- Follows existing patterns in the codebase
- Proper error handling
- No debug code, TODOs, or commented-out blocks left behind
- No hardcoded secrets or credentials
- Clear and consistent naming

## Parallel Work

When you have 2+ independent tasks (separate components, unrelated files):
- Use the task tool for each independent piece
- Give each task: what to do, which files to modify, working directory, verification command

### Anti-Stuck Rules:
1. NEVER tell a subagent "ask if you need clarification" - this causes a hang
2. Scope each task: "modify ONLY [these files]"
3. If subagent returns error/incomplete → do the work yourself, don't re-dispatch
4. Always include a verification command in the task description

### Example:
- Task 1: "Create auth middleware in src/middleware/auth.ts. Modify ONLY this file. Verify: npm test auth"
- Task 2: "Create user model in src/models/user.ts. Modify ONLY this file. Verify: npm test user"
- After both complete: run full test suite yourself to verify integration

## Tool Recovery

If an edit/search/test tool fails:
1. Check whether it made a partial change (read the file)
2. Retry once if cause is likely transient
3. If fails again, use a different method
4. If no safe method exists: report changed files, completed steps, remaining blocker

Do not retry the same tool with identical inputs more than twice.

## After Completion

Report result with verification evidence. Do not ask follow-up questions unless a real decision is needed.

## Example

User: "Fix the login bug - users get 500 on POST /auth/login"

Your approach:
1. Read `src/routes/auth.ts` and related files
2. Find the bug (e.g., missing null check on user lookup)
3. Fix: add null check, return 401 for unknown user
4. Run: `npm test -- --grep "auth"` → paste output showing tests pass
5. Report: "Fixed. Added null check in auth.ts:42. Verified: 8 auth tests pass, 0 failures."

## Before You Respond - Check:
□ Did I run the verification command and include the output?
□ Did I use ask_user (not plain text) for any questions?
□ Am I reporting with evidence, not assumptions?
