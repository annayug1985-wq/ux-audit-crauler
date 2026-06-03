# UX Audit

Hybrid UX audit skill for websites. It combines crawl output, browser interaction, and visual evidence to produce a business-oriented report with prioritized findings and actionable recommendations.

This version is designed to reduce false negatives from text-only crawling and to make the audit more defensible with screenshots, confidence levels, and explicit evidence tracking.

## What it does

The skill audits a site across six blocks:

1. Nielsen heuristics
2. Conversion
3. Content
4. Technical and visual quality
5. Information architecture
6. Accessibility quick pass

It supports:

- quick audits for small sites
- evidence-heavy audits for commercial landing pages and service sites
- large-site audits based on template sampling
- competitor comparison
- fix specifications for implementation

## Why this version is stronger

Compared with a text-only crawl workflow, this version adds:

- engine selection by job type
- explicit site mapping before evaluation
- browser checks for forms, menus, and mobile states
- screenshots as evidence
- page-template sampling for large sites
- confidence levels on every finding
- a separate evidence artifact to distinguish facts from inferences
- an accessibility quick pass by default

## Recommended tool roles

| Tool | Best use |
|---|---|
| `Playwright` | interactive states, forms, screenshots, mobile emulation, JS-heavy pages |
| `Crawlee` | scalable orchestration, representative-page crawling, retries, queueing |
| `Firecrawl` | quick map + multi-page markdown extraction |
| `Crawl4AI` | open-source structured extraction and clean markdown |
| `Scrapy` | large deterministic crawls and link graphs |
| `ScrapeGraphAI` | optional AI extraction or entity enrichment |

## Audit modes

### Quick audit

Use when the goal is triage.

- small marketing site
- limited time
- low need for screenshots

Typical stack: `Firecrawl` or `Crawl4AI`

### Evidence audit

Default mode for business websites.

- combines crawl and browser inspection
- includes screenshots
- checks key interaction states

Typical stack: `Firecrawl` or `Crawl4AI` + `Playwright`

### Large-site audit

Use for catalogs, directories, media, or documentation portals.

- map first
- classify templates
- audit representative pages

Typical stack: `Scrapy` or `Crawlee` + `Playwright`

## Working artifacts

The skill should create:

- an evidence file using `references/evidence-template.md`
- a final report using `references/report-template.md`

The evidence file exists to preserve honesty:

- what was directly observed
- what was extracted
- what was inferred
- what could not be verified

## Built-in safeguards

1. **Evidence honesty**
   Never claim that an element is absent when it may simply be hidden behind interaction or not captured by the crawler.

2. **Severity calibration**
   CRITICAL findings must truly block conversion or trust, not merely be inconvenient.

3. **Confidence labeling**
   Every finding gets High, Medium, or Low confidence.

4. **No fabricated statistics**
   Do not invent percentages or studies to make the report sound stronger.

5. **Template-aware coverage**
   Large sites are sampled by page type, not judged from the homepage alone.

## Example prompts

- `Audit this site: example.com`
- `Review the UX of this landing page and focus on forms`
- `Why is this site not converting?`
- `Check the mobile UX on example.com`
- `Compare this site with 3 competitors`
- `Turn the audit into a fix spec for design and development`

## Installation

Place the `ux-audit` folder in your Codex or Claude skills directory.

## Notes

- This skill is most valuable when the agent has access to both crawl tools and browser automation.
- If only crawl tools are available, the skill should explicitly downgrade confidence on interaction-heavy findings.
