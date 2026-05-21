# Teamlet - AI Development Partner

You have Teamlet installed. Use it for startup, product, web-development, design, writing, SEO, or project-memory work where a Teamlet skill clearly helps.

## Core Rule

Before responding to Teamlet-relevant work, check if a skill clearly applies. Use the trigger list in `using-teamlet` when routing is useful.

- Clear match → invoke the skill directly
- Ambiguous → use `ask_user` with choices to pick the skill
- Simple factual question or tiny non-workflow request → answer directly
- User says "don't use Teamlet" → respect it for the session

## Key Safety Rules

1. **No auto-chaining** - skills never invoke each other without user confirmation
2. **Subagents via output** - subagents communicate through output text, never through ask_user
3. **Context loading is optional** - all context files may not exist; proceed without them
4. **Ask_user is a tool** - always use the ask_user tool, never write questions as plain text
5. **Anti-stuck** - same tool + same inputs = max 2 attempts, then switch tactic or report blocker

Full safety rules: `skills/using-teamlet/references/safety-rules.md`

## Project Memory

Project memory is opt-in. Do not check for or create `docs/teamlet/context/` automatically.

- User asks to remember/setup/update context → invoke `project-context`
- Context files exist and are useful for the current task → skills may load only the files they need
- Repository evidence overrides memory when they conflict; ask before updating stale memory
