# UX Audit Checklist - 58 items

Use this checklist after the site has been mapped and representative pages have been selected.

Allowed statuses for each item:

- `OK`
- `Problem`
- `Could not verify`
- `Not applicable`

For each problem, record:

- priority
- confidence
- page/location
- evidence type
- recommendation

## Block 1. Nielsen heuristics (10 items)

| # | Check | Heuristic |
|---|---|---|
| 1.1 | Is there visible feedback on actions such as button click, form submit, loading, filtering, or navigation? | Visibility of system status |
| 1.2 | Does the user know where they are through active navigation, breadcrumbs, progress steps, or page context? | Visibility of system status |
| 1.3 | Does the site use the audience's language rather than internal jargon? | Match between system and the real world |
| 1.4 | Can the user go back, close overlays, undo, or escape a dead-end state? | User control and freedom |
| 1.5 | Are buttons, links, labels, CTA styles, and page patterns consistent across pages? | Consistency and standards |
| 1.6 | Are forms protected from errors with labels, hints, masks, validation, and sensible defaults? | Error prevention |
| 1.7 | Are key options visible without forcing users to remember hidden paths? | Recognition rather than recall |
| 1.8 | Are there shortcuts or accelerators for experienced users when relevant? | Flexibility and efficiency of use |
| 1.9 | Is the interface focused, without excessive noise that competes with the primary action? | Aesthetic and minimalist design |
| 1.10 | Are error messages clear, actionable, and placed close to the problem? | Help users recognize, diagnose, and recover from errors |

## Block 2. Conversion (12 items)

| # | Check | Aspect |
|---|---|---|
| 2.1 | Is it clear within the first screen what the company offers, for whom, and why it is worth choosing? | Value proposition |
| 2.2 | Is there a clear primary CTA above the fold? | CTA |
| 2.3 | Is the CTA hierarchy clean, or are there too many competing primary actions? | CTA strategy |
| 2.4 | How many fields are in the main lead form, and are they justified for first contact? | Forms |
| 2.5 | Are labels, required states, errors, and success states understandable in the form flow? | Forms |
| 2.6 | Are there alternative contact methods such as phone, messenger, chat, booking, or email? | Conversion channels |
| 2.7 | Are testimonials, cases, reviews, or portfolio items present and relevant? | Social proof |
| 2.8 | Do trust signals look specific and credible rather than generic or suspicious? | Trust |
| 2.9 | Are contact details listed clearly enough to support trust? | Trust |
| 2.10 | Is CTA repetition sensible on long pages? | CTA placement |
| 2.11 | Is there a visible confirmation or thank-you state after a conversion action? | Post-conversion |
| 2.12 | Are prices, price ranges, calculators, or qualification cues provided when appropriate for the business model? | Price transparency |

## Block 3. Content (12 items)

| # | Check | Aspect |
|---|---|---|
| 3.1 | Does the tone of voice match the market position and audience expectations? | Tone |
| 3.2 | Is there a unique and meaningful H1 on key pages? | SEO / clarity |
| 3.3 | Is the heading hierarchy logical and scannable? | Structure |
| 3.4 | Are title and description meta tags present and reasonably unique? | SEO |
| 3.5 | Do key images appear to have alt text or accessible equivalents when inspectable? | Accessibility / SEO |
| 3.6 | Is the text readable in terms of paragraph length, density, and scanability? | Readability |
| 3.7 | Are there obvious grammar, typo, or formatting issues? | Content quality |
| 3.8 | Are case studies or portfolio items outcome-oriented rather than decorative? | Proof / storytelling |
| 3.9 | Is the content current, with no obviously outdated offers, dates, or stale references? | Freshness |
| 3.10 | If there is a blog or news section, does it support trust or signal abandonment? | Activity |
| 3.11 | Does the copy focus on customer outcomes rather than only company self-description? | Customer-centricity |
| 3.12 | Is there an FAQ or equivalent path to common objections? | Information completeness |

## Block 4. Technical and visual quality (10 items)

| # | Check | Aspect |
|---|---|---|
| 4.1 | Does HTTPS work and avoid mixed-trust signals? | Security |
| 4.2 | Is the site usable on mobile viewport(s)? | Mobile |
| 4.3 | Are there broken links, blank states, missing assets, or obvious script failures? | Reliability |
| 4.4 | Does the site load without major perceived delay on key pages? | Speed |
| 4.5 | Do images and media display correctly? | Visual integrity |
| 4.6 | Does core content remain understandable if JS features fail or lag? | Resilience |
| 4.7 | Is the browser tab title and favicon present and sensible? | Basics |
| 4.8 | Is there horizontal scroll or clipped content on mobile? | Mobile |
| 4.9 | Do sticky elements block content, inputs, or CTA visibility on smaller screens? | Mobile / layout |
| 4.10 | Are modal, chat, cookie, or promo overlays manageable rather than conversion-hostile? | Interaction quality |

## Block 5. Information architecture (8 items)

| # | Check | Aspect |
|---|---|---|
| 5.1 | Is the navigation structure logical for the user's mental model? | Navigation |
| 5.2 | Can key pages be reached in a small number of steps? | Depth |
| 5.3 | Is the main menu focused rather than overloaded? | Width |
| 5.4 | Is there search when the volume or complexity of content calls for it? | Findability |
| 5.5 | Are breadcrumbs or comparable orientation aids present on deeper pages? | Orientation |
| 5.6 | Does the footer repeat key navigation and trust links? | Support navigation |
| 5.7 | Are services/products grouped in a way that avoids overlap and confusion? | Categorization |
| 5.8 | Is there an XML or HTML sitemap, or at least a discoverable crawl structure? | Structure |

## Block 6. Accessibility quick pass (6 items)

| # | Check | Aspect |
|---|---|---|
| 6.1 | Do primary text and CTA elements appear to have adequate contrast by visual inspection? | Contrast |
| 6.2 | Are forms labeled clearly enough for sighted and assistive-tech users? | Forms |
| 6.3 | Are focus indicators visible if keyboard interaction is tested? | Keyboard |
| 6.4 | Are touch targets likely large enough on mobile? | Mobile accessibility |
| 6.5 | Is page structure understandable through headings and landmarks? | Semantic structure |
| 6.6 | Are images, icons, and controls likely to have meaningful names or alternatives where needed? | Non-text content |

## Verification notes

- Prefer browser evidence over crawl inference for menus, popups, forms, sticky UI, and mobile states.
- On large sites, evaluate page templates, not random individual URLs.
- If a claim depends on an interaction you did not perform, mark it `Could not verify`.
- If accessibility cannot be measured exactly, state that the item is a risk estimate, not a conclusive failure.
