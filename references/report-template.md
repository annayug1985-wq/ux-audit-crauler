# UX Audit report template

Write the report in the same language the user speaks.

```markdown
# UX Audit: [Site name / URL]
**Date:** [date]
**Auditor:** Codex (UX Audit Skill)
**Audit mode:** Quick audit / Evidence audit / Large-site audit

## Executive summary

**Overall score:** [X/10] - [short interpretation]
**Problems found:** [N] critical, [N] major, [N] minor
**Confidence profile:** [brief note on coverage and confidence]

### Top findings
1. [Finding 1]
2. [Finding 2]
3. [Finding 3]
4. [Finding 4]
5. [Finding 5]

### Strengths
- [Strength with business relevance]
- [Strength with business relevance]

---

## Audit context

**Site:** [URL]
**Industry:** [industry or inferred]
**Target audience:** [description or inferred]
**Main conversion goal:** [goal or inferred]
**Priority device context:** [mobile-first / desktop-first / mixed]
**Pages audited:** [list]
**Representative templates reviewed:** [list]
**Tools used:** [crawl/browser tools]

---

## Evidence notes

**Evidence artifact:** [path]
**Visual evidence available:** [yes/no + screenshot paths]
**Important limitations:**
- [e.g. no browser automation available]
- [e.g. gated content not inspected]
- [e.g. form not fully submitted by scope]

---

## Block 1. Nielsen heuristics

### Problem 1.X: [Title]
- **Priority:** CRITICAL / MAJOR / MINOR
- **Confidence:** High / Medium / Low
- **Heuristic:** [violated heuristic]
- **Where:** [page / section / element]
- **Evidence type:** Observed / Extracted / Inferred
- **What was observed:** [factual description]
- **Why it matters:** [user impact + business impact]
- **What to do:** [specific action]
- **Expected effect:** [improvement]
- **Evidence reference:** [screenshot, URL, evidence record]

### Items without problems
- [1.X] [Title] - OK: [brief note]

### Could not verify
- [1.X] [Title] - [why verification was not possible]

---

## Block 2. Conversion
[same structure]

## Block 3. Content
[same structure]

## Block 4. Technical and visual quality
[same structure]

## Block 5. Information architecture
[same structure]

## Block 6. Accessibility quick pass
[same structure]

---

## Prioritized fix plan

### CRITICAL - act immediately
| # | Problem | Block | Action | Expected impact | Effort |
|---|---|---|---|---|---|

### MAJOR - next sprint
| # | Problem | Block | Action | Expected impact | Effort |
|---|---|---|---|---|---|

### MINOR - backlog
| # | Problem | Block | Action | Expected impact | Effort |
|---|---|---|---|---|---|

---

## Recommended sequence

1. [Highest-leverage action]
2. [Second action]
3. [Third action]

---

## Competitor benchmark (if conducted)

| Parameter | [Client] | [Competitor 1] | [Competitor 2] |
|---|---|---|---|
| Value proposition clarity |  |  |  |
| CTA visibility |  |  |  |
| Form friction |  |  |  |
| Trust signals |  |  |  |
| Pricing transparency |  |  |  |
| Mobile usability |  |  |  |

---

## Methodology

This audit combines crawl extraction, representative-page review, and browser-based inspection where available. Findings are prioritized by business impact and labeled by confidence. Interaction-heavy elements such as menus, forms, and mobile states are treated cautiously when direct evidence is limited.
```
