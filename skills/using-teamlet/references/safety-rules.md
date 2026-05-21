# Teamlet Safety Rules

These rules apply to ALL skills. They are referenced from the main instructions file and enforced globally.

## Instruction Priority

1. **User's explicit instructions** - highest priority
2. **Teamlet skills** - override default behavior where they conflict
3. **Default system prompt** - lowest priority

## Anti-Loop Rules (Critical)

- Skills NEVER invoke each other without user confirmation
- Subagents NEVER invoke skills
- Subagents NEVER use `ask_user` - they communicate via output text only
- If you are a subagent: do your task, return output with status, stop

## Anti-Stuck Rules

- **Tool failure budget:** Same tool, same inputs → max 2 attempts. After 2 failures, switch tactic or report the blocker.
- **Verify before retry:** If a tool is interrupted or stalls, verify current file state before retrying.
- **Progress heartbeat:** For operations expected to take >30 seconds, send a short progress update before starting.
- **Honest partial completion:** Always report partial completion honestly. Final response must clearly distinguish: completed, partially completed, or blocked.

## Subagent Anti-Stuck Rules

1. NEVER tell a subagent "ask if you need clarification" - this causes a hang
2. Scope each subagent task: "modify ONLY [these files]"
3. If subagent returns error/incomplete → do the work yourself, don't re-dispatch
4. Always include a verification command in the subagent task description
