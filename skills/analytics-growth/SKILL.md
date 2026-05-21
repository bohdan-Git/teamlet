---
name: analytics-growth
description: "Use for funnels, event tracking, activation metrics, retention analysis, pricing experiments, and growth strategy. Measurement-first approach for solo founders."
---

# Analytics & Growth - Measure, Learn, Grow

Data-driven decisions for solo founders. No vanity metrics, no complex tooling overkill.

## When to Use

- "How do I track signups/conversions?"
- "What metrics should I watch?"
- "Set up event tracking for X"
- "Is my pricing working?"
- "How do I improve retention?"

## Context

Read `docs/teamlet/context/brief.md` for product phase and audience.
If the file doesn't exist, proceed without it.

## Process

1. Ask current phase and what they're trying to learn (1 question via `ask_user`):
   > choices: ["Exploring/MVP - did anyone get value?", "MVP live - do they come back?", "Growing - full funnel optimization"]
2. Recommend 3-5 metrics appropriate to their phase
3. Propose tracking implementation (tool + key events)
4. Get approval before implementing

**If user says "quick":** Direct answer with specific metric/tool/implementation recommendation. No audit.
**If user says "thorough":** Full measurement strategy: map funnel, design event taxonomy, recommend tooling, write plan to `docs/teamlet/plans/YYYY-MM-DD-analytics.md`.

## Core Metrics Framework

| Layer | Metric | Example |
|---|---|---|
| Acquisition | How users find you | Signups/week, traffic source |
| Activation | First value moment | Completed onboarding, first [core action] |
| Retention | Users who come back | Day 7 / Day 30 return rate |
| Revenue | Money in | MRR, conversion to paid, ARPU |
| Referral | Users who bring others | Invite rate, NPS |

**Phase-appropriate focus:**
- Exploring/MVP → Activation only
- MVP live → Activation + Retention
- Growing → Full funnel + Revenue

## Event Tracking Principles

1. **Name events by user action**: `completed_checkout` not `clicked_button_3`
2. **Minimal properties**: user_id, timestamp, 2-3 contextual fields max
3. **One source of truth**: one analytics tool, not events scattered across 5 services
4. **Track decisions, not pageviews**: actions indicating intent > passive browsing

## Tool Recommendations (Solo-Founder Scale)

| Need | Recommended | Why |
|---|---|---|
| Product analytics | PostHog or Mixpanel | Event-based, funnel visualization |
| Web analytics | Plausible or Fathom | Privacy-first, simple |
| Error tracking | Sentry | Actionable errors |
| Session replay | PostHog (built-in) | See what confused users |

## Pricing & Experiments

- Test pricing early - easier to raise at 10 users than 10,000
- A/B test only one variable at a time
- Measure willingness to pay by behavior, not surveys
- Grandfather existing users when changing prices

## Example

User: "What metrics should I track for my SaaS?"

Your approach:
1. Ask phase via ask_user: choices: ["Exploring/MVP", "MVP live, getting users", "Growing, optimizing"]
2. If "MVP live": recommend Activation + Retention metrics:
   - Activation: "User completes first [core action] within 24h of signup"
   - Retention: "Day 7 return rate"
   - Revenue: "Free-to-paid conversion rate" (track but don't optimize yet)
3. Propose: PostHog (free tier), 3 key events: `signed_up`, `completed_first_action`, `returned_day_7`
4. Ask: "Want me to implement the tracking code?" choices: ["Yes, implement", "Just the plan", "Done"]
