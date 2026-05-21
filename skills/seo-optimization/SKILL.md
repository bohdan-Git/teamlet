---
name: seo-optimization
description: "Use for SEO audits, meta tags, Open Graph, structured data (JSON-LD), sitemap, robots.txt, Core Web Vitals, semantic HTML, keyword strategy."
---

# SEO Optimization - Technical & On-Page SEO

Everything a solo developer needs to rank. No agency required.

## When to Use

- SEO audit of a page or site
- Add/fix meta tags, Open Graph, structured data
- Fix robots.txt, sitemap, canonicals
- Core Web Vitals issues
- Keyword strategy for a page

## Context

Read `docs/teamlet/context/brief.md` for product and audience info.
Read `docs/teamlet/context/stack.md` for framework details (Next.js, Nuxt, etc.).
If files don't exist, proceed without them.

## Process

1. **Scan** - check existing SEO setup (meta tags, sitemap, robots.txt, structured data)
2. **Audit** - run checklist sections relevant to the request
3. **Report** - categorize findings:
   ```
   🔴 Critical: [issue] - [impact] - [fix]
   🟡 Important: [issue] - [impact] - [fix]
   🟢 Good: [what is correct]
   💡 Opportunity: [enhancement]
   ```
4. **Ask before fixing** via `ask_user`:
   > choices: ["Yes, fix Critical items", "Show full report first", "I will fix manually"]
5. **Implement** approved fixes
6. **Verify** - re-check after changes

**If user says "quick":** Fix a specific known issue directly. No audit.
**If user says "thorough":** Full site audit + prioritized action plan + per-item approval.

If scope is unclear, ask once via `ask_user`: choices: ["Full site audit", "Specific page audit", "Fix a known issue"]

## Audit Checklist

**Technical:** canonical tags, robots.txt, sitemap.xml, HTTPS, mobile-friendly, no broken links
**Meta:** unique title (50-60 chars), meta description (150-160 chars), one H1 per page
**Open Graph:** og:title, og:description, og:image (1200×630px), og:url, og:type
**Structured Data (JSON-LD):** Organization, WebPage/Article, BreadcrumbList
**Core Web Vitals:** LCP < 2.5s, CLS < 0.1, INP < 200ms
**Content:** one primary keyword per page, keyword in H1 + first paragraph, internal links

Framework notes:
- **Next.js / Nuxt**: use built-in metadata API
- **SPA**: SSR or SSG required for SEO-critical pages

## Measurement Protocol

1. **Baseline** before changing - record current metrics or note "no baseline available"
2. **Predict** impact - state expected improvement and why
3. **Verify** after changing - re-measure and report delta
4. If measurement is impractical (local dev): state the rationale clearly

## Startup SEO Priority Order

1. Crawlability (robots.txt, sitemap, no broken links)
2. Title / meta description / H1
3. Canonical URLs / HTTPS
4. Structured data (Organization, WebPage)
5. Internal linking
6. Performance (LCP, CLS)
7. Content expansion and keyword strategy

## Example

User: "Audit SEO for my homepage"

Your approach:
1. Scan: read index page, check for meta tags, robots.txt, sitemap
2. Audit against checklist
3. Report:
   - 🔴 Critical: Missing meta description - hurts CTR in search results - add `<meta name="description" content="...">`
   - 🟡 Important: No Open Graph image - social shares look plain - add og:image (1200×630px)
   - 🟢 Good: Title tag present, H1 hierarchy correct, HTTPS active
   - 💡 Opportunity: Add JSON-LD Organization schema for knowledge panel
4. Ask: "Found 1 critical, 1 important issue. Fix critical now?" choices: ["Yes, fix Critical items", "Show full report", "I'll fix manually"]

## Before You Respond - Check:
□ Did I scan actual files before reporting (not guessing)?
□ Did I categorize findings (🔴🟡🟢💡)?
□ Did I ask before making any edits?
□ Am I making measurable claims with evidence?
