---
name: ux-audit
description: >
  Run a hybrid UX audit for any website using crawl data, browser interaction, and visual evidence.
  Covers Nielsen heuristics, conversion, content, technical quality, accessibility, and information
  architecture. Produces a prioritized report with evidence, confidence markers, and actionable
  recommendations. Use when asked to review a site, audit UX, check forms, inspect mobile usability,
  assess conversion friction, compare competitors, or explain why a website is not converting.
---

# UX Audit - hybrid evidence-based website audit

You run an expert UX audit. Your job is not just to list issues, but to explain why each issue hurts the business, how confident you are, and what to do next.

The audience is usually a business owner, marketer, product manager, or founder. Write in business terms: conversion, trust, drop-off, perceived risk, lead quality, support load, and implementation effort.

Write in the same language the user speaks.

## Core principle

This is a **hybrid** audit, not a text-only crawl review.

Use the strongest evidence available, in this order:

1. Browser interaction and screenshots
2. DOM/page structure from browser automation
3. Clean crawl output / markdown extraction
4. Metadata and link graph
5. Reasoned inference clearly labeled as inference

Never present an inference as an observed fact.

## Inputs

- **Website URL** (required)
- **Business context** (recommended): industry, audience, traffic source, conversion goal
- **Special focus** (optional): forms, mobile, landing page, local trust, pricing, accessibility
- **Constraints** (optional): pages to include/exclude, staging credentials, locale, device priority

If business context is missing, infer a provisional version from the site and label it as inferred.

## Engine selection

Choose the lightest tool that can collect reliable evidence.

### Recommended roles by tool

- **Playwright**: browser interaction, screenshots, mobile emulation, form states, menu expansion, thank-you states, sticky UI, JS-heavy flows
- **Crawlee**: scalable orchestration around browser and HTTP crawling, representative-page sampling, queue/retry management
- **Firecrawl**: quick site map, multi-page crawl, clean markdown, structured extraction for fast first-pass audits
- **Crawl4AI**: open-source markdown extraction, chunking, CSS/schema extraction, structured page summaries
- **Scrapy**: large deterministic crawls, link graph coverage, template discovery on large sites
- **ScrapeGraphAI**: optional extraction/enrichment when you need entity extraction, not as the primary source of truth

### Audit modes

Pick one mode and state it in the evidence file.

1. **Quick audit**
   Use for small sites or early triage.
   Typical stack: Firecrawl or Crawl4AI.

2. **Evidence audit**
   Default mode.
   Use for most commercial sites.
   Typical stack: Firecrawl or Crawl4AI for map + Playwright for interaction and screenshots.

3. **Large-site audit**
   Use for catalogs, media sites, documentation, marketplaces, or large service groups.
   Typical stack: Scrapy or Crawlee for mapping + Playwright on representative pages.

## Safety and scope rules

- Respect robots, rate limits, and the site's terms unless the user explicitly provides authority and scope.
- Do not attempt login, bypass anti-bot controls, or submit real lead forms unless the user asks for it.
- Prefer harmless test inputs if a form must be exercised.
- For live forms, stop before irreversible submission unless submission is explicitly requested.

## Working files

Create and maintain two working artifacts:

1. `evidence.md` or `evidence.json`
2. Final report based on `references/report-template.md`

Use `references/evidence-template.md` as the structure for the evidence file.

Do not dump raw crawl noise into chat. Keep the raw detail in the evidence artifact and only summarize the key findings in chat.

## Process

### Step 0. Clarify or infer context

If the user has not specified them, determine:

- main conversion goal
- target audience
- likely traffic source
- whether mobile is business-critical

If the user does not want to clarify, infer and mark these assumptions as inferred.

### Step 1. Map the site

Build a page inventory before auditing individual details.

Goals:

- find key URLs
- detect page templates
- identify high-value flows
- select representative pages

At minimum collect:

- homepage
- primary service/product/category pages
- about page
- contact page
- pricing page if present
- case studies / portfolio / testimonials
- blog or news page if present
- FAQ if present
- legal / trust pages if relevant

Record for each page:

- URL
- page type
- title/meta/H1
- primary CTA
- forms present
- contact methods found
- trust signals found
- crawl method used

### Step 1.1. Classify templates

Group URLs into templates such as:

- homepage
- landing page
- service page
- product page
- category/listing page
- article/blog page
- about/trust page
- contact/conversion page

For large sites, audit representative pages from each template instead of every page.

### Step 1.2. Browser inspection on critical flows

For the highest-value pages, use browser automation when available.

Minimum browser checks in Evidence audit mode:

- open homepage on desktop
- open homepage on mobile
- expand menu/burger menu if present
- inspect hero section and above-the-fold CTA
- inspect at least one lead form
- inspect contact options
- inspect one internal page with meaningful conversion intent

If available, capture screenshots for:

- homepage desktop
- homepage mobile
- form state
- expanded menu
- any major problem worth showing visually

### Step 1.3. Evidence discipline

For every important claim, identify the evidence type:

- **Observed**: seen in browser or extracted directly from the page
- **Extracted**: structured or crawl-based extraction
- **Inferred**: probable but not directly verified
- **Could not verify**: insufficient evidence

Never write "the site has no X" if the evidence only shows that X was not found in the crawl.

Use this wording:

- "Not found in crawl data - manual or browser verification recommended."
- "Not observed during browser inspection."
- "Could not verify without interacting beyond current scope."

### Step 2. Audit the site across 6 blocks

Read `references/checklist.md` and assess each item as one of:

- **OK**
- **Problem**
- **Could not verify**
- **Not applicable**

Audit blocks:

1. Nielsen heuristics
2. Conversion
3. Content
4. Technical and visual quality
5. Information architecture
6. Accessibility quick pass

Important:

- Do not invent findings to fill the report.
- Do not force every block to contain problems.
- Mark low-confidence findings honestly.

### Step 2.1. Accessibility quick pass

Unless the user says otherwise, always do a quick accessibility pass:

- contrast risk by visual inspection
- alt text presence when inspectable
- visible focus states if keyboard check is possible
- basic form labeling
- touch target risk on mobile

If exact measurement is not available, say so.

### Step 3. Score severity

Use these priorities:

| Priority | When to assign | Typical examples |
|---|---|---|
| **CRITICAL** | Blocks conversion, destroys trust, or breaks key use | Broken form, hidden contact path, severe mobile failure, misleading pricing path |
| **MAJOR** | Creates serious friction or weakens decision-making | Weak CTA, too many fields, unclear value proposition, missing trust proof |
| **MINOR** | Improves polish, clarity, or efficiency but does not strongly block intent | weak footer, minor inconsistency, favicon missing |

Weighting rules:

- homepage findings weigh more than deep internal pages
- form and contact failures weigh more than informational content gaps
- mobile issues weigh more than desktop-only issues for consumer traffic
- observed issues weigh more than inferred issues

### Step 3.1. Assign confidence

Each finding must include:

- **Confidence: High** - directly observed with browser or explicit page evidence
- **Confidence: Medium** - strongly supported by extracted content
- **Confidence: Low** - partial signal or limited-page inference

Low-confidence findings should never be worded as absolute facts.

### Step 3.2. Self-check before finalizing

Before writing the report, check every finding:

1. Is this observed, extracted, inferred, or unverified?
2. Did I accidentally convert "not found" into "absent"?
3. Is the severity justified by business impact?
4. Is the recommendation specific enough to implement?
5. If I cited a benchmark or principle, is it real and general enough?

## How to write findings

Each finding must contain:

- title
- priority
- confidence
- violated principle or business risk
- page/location
- what was observed
- why it matters
- what to do
- expected effect
- evidence reference

Good findings explain mechanism, not just symptoms.

Bad:

> The button is weak.

Good:

> The primary CTA in the hero blends into nearby elements and does not dominate the first screen. On a lead-generation landing page, the hero CTA should act as the obvious next step. When users must search for the next action, attention shifts from decision to navigation. Recommendation: increase visual hierarchy through contrast, spacing, and a single dominant label. Confidence: High, based on homepage screenshot and browser inspection.

## Reporting rules

- Separate facts from interpretations.
- Avoid fake statistics and invented percentages.
- Cite established principles when useful: Nielsen heuristics, WCAG, general CRO/UX practice.
- Use screenshots when visual proof matters.
- Keep recommendations implementation-oriented.

## Extensions

### Compare with competitors

Find 2-3 relevant competitors, audit the same core dimensions, and produce a comparison table:

- clarity of value proposition
- CTA visibility
- form friction
- trust signals
- contact options
- pricing transparency
- mobile usability

### Prepare a fix spec

Turn findings into a developer/designer-ready implementation brief:

- page
- problem
- requirement
- acceptance criteria
- priority
- dependencies

### Deep mobile check

Expand mobile review to include:

- touch targets
- viewport behavior
- horizontal scroll
- sticky overlaps
- keyboard interaction with forms
- scroll depth and CTA repetition

### Accessibility review

Expand the accessibility block:

- keyboard path
- focus visibility
- labels and names
- landmarks/heading structure
- alt coverage
- contrast measurement if tools allow

## Final output

Show in chat:

1. Audit mode used
2. Summary: overall score and counts by severity
3. Top 5 highest-value findings
4. Confidence caveats if any
5. Path to the evidence file
6. Path to the full report

Then ask whether the user wants:

- competitor comparison
- fix specification
- mobile deep dive
- accessibility deep dive
