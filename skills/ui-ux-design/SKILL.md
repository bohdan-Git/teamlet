---
name: ui-ux-design
description: "Use when designing, building, or reviewing UI. Covers visual design, accessibility, responsive layout, component patterns."
---

# UI/UX Design - Design Director

Build distinctive, production-grade interfaces: visually strong AND solid UX foundations.

## When to Use

- New page or component design
- UI redesign or visual refresh
- Accessibility review
- Responsive layout fixes
- Design system setup

## Context

Read `docs/teamlet/context/brief.md` for audience and design constraints.
Read `docs/teamlet/context/stack.md` for design system/component library info.
If files don't exist, proceed without them.

## Process

1. **Understand** - component/page, goal, audience
2. **Direction** - derive from existing design system. If no existing styles, ask once via `ask_user`: choices: ["Minimal & clean", "Bold & expressive", "Derive from existing styles", "Let me describe it"]
3. **Build** - real, working code (semantic HTML, CSS custom properties, responsive, accessible)
4. **Accessibility pass** - WCAG 2.1 AA checklist
5. **Responsive pass** - all breakpoints (320px minimum)
6. **Present** via `ask_user`: choices: ["Looks great", "Tweak the design", "Different direction"]

**If user says "quick":** Fix or tweak existing UI directly. No design discussion.
**If user says "thorough":** Explore 2-3 direction variants before building. Iterative refinement.

## Design Defaults (Use These Unless Brand Exists)

**Typography:**
- Font pairing: one display/heading font + one body font
- Avoid Inter/Roboto/Arial alone unless the project already uses them
- Typographic scale: 1.2-1.5 ratio

**Color:**
- 1 primary, 1 sharp accent, neutral base, 1 semantic red
- Never pure black text (#0a0a0a not #000)
- Min contrast: 4.5:1 body, 3:1 large text (WCAG AA)

**Spacing:** consistent scale (4/8/16/24/32/48px). No magic numbers.

**Distinctiveness (avoid generic AI output):**
- ✅ Distinctive font pairings when designing from scratch
- ✅ Cohesive palette with sharp accents
- ✅ Asymmetry, overlap, diagonal flow where appropriate
- ✅ Respect existing brand/design system first

## Accessibility (Non-Negotiable)

- Touch targets ≥ 44×44px
- Keyboard accessible: Tab navigation, Enter/Space activation
- Semantic HTML: button for actions, a for navigation, correct heading hierarchy
- All images have alt text. Icons have aria-label or aria-hidden.
- No motion by default if `prefers-reduced-motion`
- Works at 320px width, no horizontal scroll

## When Reviewing Existing UI

```
✅ Good: [specific]
⚠️ Issue: [problem] → [fix with code example]
🎨 Design: [improvement opportunity]
♿ A11y: [gap] → [fix]
```

## Output

Write real, working code - not pseudocode:
- Semantic HTML
- CSS with custom properties, full aesthetic executed
- Responsive at all breakpoints
- Accessibility baked in

## Example

User: "Design a pricing section with 3 tiers"

Your approach:
1. Understand: pricing page, goal = convert free → paid, audience = solo developers
2. Direction: derive from existing styles (check codebase for existing CSS vars/design tokens)
3. Build: 3-card layout, semantic HTML, responsive (stack on mobile), highlighted "recommended" tier
4. Accessibility: buttons labeled clearly, contrast checked, keyboard navigable
5. Responsive: cards stack vertically at <640px, 2-col at tablet, 3-col at desktop
6. Present and ask for feedback
