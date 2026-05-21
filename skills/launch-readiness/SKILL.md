---
name: launch-readiness
description: "Use before shipping: checklist covering UX, SEO, analytics, error handling, legal basics, performance, onboarding, and payment flow."
---

# Launch Readiness - Pre-Ship Checklist

Everything to check before going live. One skill replaces PM, QA, and ops review.

## When to Use

- "Am I ready to launch?"
- "What am I forgetting before shipping?"
- "Pre-launch checklist"
- About to deploy to production

## Context

Read `docs/teamlet/context/brief.md` and `docs/teamlet/context/stack.md` for product and deployment info.
If files don't exist, proceed without them.

## Process

1. Determine scope. If unclear, ask via `ask_user`: choices: ["Full web app (public, with payments)", "Web app (public, free)", "Internal tool", "API / developer product"]
2. Run checklist against the deployed/deployable app (skip sections that don't apply)
3. Report categorized findings:
   ```
   🔴 Blocker: [issue] - [how to fix]
   🟡 Important: [issue] - [how to fix]
   🟢 Nice: [issue] - [quick fix]
   ✅ Pass: [category] checks pass
   ```
4. Ask via `ask_user`: "Found [N] blockers and [M] important issues. Fix blockers now?" choices: ["Fix blockers", "Show full report first", "I'll handle it"]
5. Implement approved fixes
6. Re-verify after fixes

**If user says "quick":** Run 🔴 Critical items only. Report pass/fail. "Ready to ship" or "N blockers remain."
**If user says "thorough":** Full audit + competitive comparison + remediation plan + implementation with per-item approval.

## Checklist

### 🔴 Critical (Must fix before launch)

**Payment & Money:**
- Payment flow works end-to-end (test with real/sandbox card)
- Failed payment shows clear error + recovery path
- Pricing page matches actual charge amounts
- Subscription cancellation works and is findable

**Auth & Security:**
- Login/signup/logout works
- Password reset flow works
- No secrets in client-side code or public repo
- HTTPS everywhere (no mixed content)

**Core UX:**
- Primary user flow works without errors
- Error states show helpful messages (not stack traces)
- Empty states guide users (not blank screens)
- Loading states exist (no frozen UI)
- Works on mobile (320px minimum)

### 🟡 Important (Should fix, won't block launch)

**SEO:** Unique title + meta description, Open Graph tags, robots.txt, sitemap, canonical URLs
**Performance:** LCP < 2.5s, images optimized, no render-blocking resources
**Analytics:** Core activation event tracked, error tracking active, uptime monitoring
**Onboarding:** New user reaches value in ≤3 steps, no unnecessary required fields

### 🟢 Nice to Have (Post-launch polish)

**Legal:** Privacy policy, terms of service, cookie consent (if EU + cookies), contact method
**Polish:** Favicon, helpful 404 page, keyboard navigation, print styles

## Key Principles

- **Blockers only block** - don't let 🟢 items delay a launch
- **Evidence-based** - check actual behavior, not assumptions
- **Scope-appropriate** - skip what doesn't apply
- **Ship imperfect** - a launched product with 🟡 issues beats one that never ships

## Example

User: "Am I ready to launch?"

Your approach:
1. Ask scope: choices: ["Full web app (public, with payments)", "Web app (public, free)", "Internal tool", "API"]
2. User picks "Web app (public, with payments)"
3. Run full checklist. Scan actual code/deployment for each item.
4. Report: "🔴 2 blockers: missing HTTPS on checkout page, no error handling on payment failure. 🟡 3 important: no Open Graph image, no error tracking, LCP 3.1s. ✅ Pass: auth, core UX, mobile."
5. Ask: "Fix 2 blockers now?" choices: ["Fix blockers", "Show full report", "I'll handle it"]

## Before You Respond - Check:
□ Did I check actual code/behavior (not guessing)?
□ Did I categorize findings correctly (🔴🟡🟢)?
□ Did I skip sections that don't apply to this product type?
□ Did I ask before making any fixes?
