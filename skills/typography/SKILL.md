---
name: typography
description: Audit and refine the typography of any user interface or codebase using the craft principles from Robert Bringhurst's "The Elements of Typographic Style." Use this skill whenever the user wants to review, critique, improve, or systematize typography — in a UI, design system, component library, stylesheet, screenshot, or app. This includes requests to "make the type better," "fix the hierarchy," "clean up our fonts," build a type scale or typographic design tokens, audit CSS for type problems, or judge a screen's readability and visual hierarchy. Trigger even when the user never says "typography" by name — if they are working on headings, labels, font sizes, line spacing, tables of numbers, buttons, or the general polish of an interface's text, this skill applies.
---

# Typographic Craft

Apply the principles of Robert Bringhurst's *The Elements of Typographic Style* to screens and code. Bringhurst wrote for print, but the enduring ideas — hierarchy, restraint, honoring content, consistency, and correct detail — transfer directly. A few print-specific rules need translation for screens; those translations are noted below. The job is to audit typography against these principles and then fix it, preferably by systematizing the fix rather than patching individual screens.

## The governing idea

Typography exists to serve content. Good typographic work is mostly invisible — it guides the reader without calling attention to itself. Bringhurst's test for typography is that it should invite the reader in, reveal the structure and meaning of the content, and produce an "energetic repose": the calm, alert state in which sustained reading happens. Hold every interface to that standard. While auditing, keep asking one question: *does the type help the content lead, or does it compete with it?*

## How to apply this skill

### 1. Establish context first

The principles are weighted differently for different products, so never audit blind. Determine:

- **What kind of interface is this?** A dense data tool (dashboard, trading app, admin panel), a reading experience (article, docs, marketing site), or an expressive brand surface. Each shifts the emphasis.
- **Where is the running prose, if any?** Rules about measure and leading govern paragraphs. An interface with no paragraphs is judged almost entirely on hierarchy, figures, and consistency — say so rather than forcing reading-rhythm advice onto a dashboard.
- **Working from a screenshot or from code?** From code, read the stylesheets, theme/token files, and component styles to inventory the actual values. From an image, observe carefully and estimate.

State this context at the top of the audit so the reader knows which findings carry the most weight.

### 2. Inventory the typography

Build a quick, factual picture before judging anything:

- The typeface(s) in use, and how many.
- The set of font sizes, weights, line-heights, and letter-spacing values actually in use. In a codebase, grep the stylesheets and token files for these; in an image, estimate them.
- Where capitalization is applied — all-caps, small caps, sentence case — and how consistently.
- Where numbers appear, especially in tables or columns of figures.

A messy inventory (twelve sizes, five weights, three casing systems) is itself a finding.

### 3. Audit against the checklist

Walk the checklist below. For each issue found, note *what* is wrong, *which principle* it violates, and *the fix*. Order findings by impact, not by checklist order — the biggest legibility or hierarchy problem goes first.

### 4. Prefer systematized fixes

Default to *systematizing* rather than patching. A one-off edit fixes one screen; a token or shared text style fixes every screen and stops the problem recurring. Turn findings into design tokens or shared text-style classes with **semantic names** (`text-display`, `text-label`, not `text-18px`), because semantic names survive rebrands and theme changes. Patch directly only when a codebase has no token layer and introducing one is out of scope.

### 5. Apply or deliver

- **In a codebase:** make minimal, reversible edits. Introduce or extend the token layer, route components through it, and explain the reasoning in comments or the summary. Do not silently restyle large surfaces — show the plan first if the change is broad.
- **Review only:** deliver the audit plus a concrete token/style recommendation the team can adopt.
- Always end with what is *already* working, so the team preserves it.

## The audit checklist

**Hierarchy and casing.** Caps exist for emphasis; when every label, header, and button is all-caps, the hierarchy collapses and nothing leads. Reserve uppercase for a single tier (usually section titles). Demote labels and column headers to small caps or sentence case. Make the content — body text, data values — visually out-rank the chrome around it. Watch for two casing systems competing in one product (e.g. a sentence-case toolbar beside an all-caps everything-else).

**The modular scale.** Type sizes should be a small, deliberate set drawn from a consistent ratio — fine gradations at small sizes, wider jumps as type grows, in the spirit of the traditional typographic scale. A flat interface where everything sits at one size has no hierarchy; a chaotic one with a dozen near-identical sizes has no system. Name sizes semantically by role.

**Weight and restraint.** Few weights, used with purpose — typically three (regular, medium, semibold). Bold should be rare. Use one or two type families; if two, make them clearly contrasting, never subtly similar. Never artificially stretch or condense letterforms.

**Rhythm and spacing.** Spacing should follow a consistent system (commonly a 4px or 8px base) — the screen equivalent of a baseline grid. Line-height should be tied to that system and scaled to context: generous for body text, tighter for headings and single-line values.

**The measure.** For running text, keep lines to roughly 45–75 characters. On screen this means a `max-width` on text containers so paragraphs don't stretch the full width of a wide monitor. Longer measures need more line-height.

**Figures.** Numbers in tables or columns must use tabular (monospaced) lining figures and be right- or decimal-aligned, so digits stack and magnitudes are comparable. Proportional or old-style figures are fine in running prose. Never apply letter-spacing to figures.

**Analphabetic detail.** Use real typographic marks: curly quotation marks and apostrophes, en dashes for ranges, em dashes for breaks in thought — not double hyphens. Use a true minus sign for negative numbers where it matters (finance, data). Use proper ligatures, and small caps for acronyms set in running text so they don't shout. Keep number and currency formatting consistent: one precision rule and one currency notation per data type.

**Letterspacing.** Never letterspace lowercase text. Letterspacing capitals and small caps is correct and often necessary.

**Structural forms.** Treat like elements alike — parallel sections should be set in parallel. The first paragraph after a heading needs no indent (an indent marks a break from a *preceding* paragraph). Use either paragraph indentation or paragraph spacing, not both.

**Honoring content / energetic repose.** Interface chrome — labels, captions, secondary controls — should recede so the actual content leads. If a screen feels noisy, the usual cause is chrome that is too loud: too large, too bold, too high-contrast, or all-caps. Quiet it down.

**Screen adaptations Bringhurst did not cover.** Always also check: sizes set in relative units (`rem`) so type respects the user's browser/OS settings; text contrast meeting WCAG minimums and sensible minimum sizes; a scale that adapts across breakpoints; weight that may need lightening on dark backgrounds; and font loading that avoids flashes of invisible or unstyled text.

## Output format

Structure the audit like this:

```
## Typographic audit — [interface or codebase name]

**Context** — [interface type; where prose lives; basis: code or screenshot].
[One line on which principles therefore weigh most.]

**Findings** (ordered by impact)
For each finding:
  - A short, specific heading.
  - What is wrong (concrete and observed, not vague).
  - The principle behind it.
  - The fix.

**Systematized recommendation**
The design tokens or shared text styles that encode the fixes, with
semantic names. Where formatting rules are not expressible in CSS
(number precision, currency notation), state them as an explicit
formatting contract.

**What's already working**
Credit what is correct so the team preserves it.
```

Keep findings concrete. "Hierarchy is weak" is not actionable; "every column header, field label, and button is all-caps, so uppercase no longer signals anything" is.

## Principles for the fixes

- **Restraint is the default.** Most typographic problems are solved by *removing* — fewer sizes, fewer weights, fewer casing systems, less letterspacing — not by adding.
- **Systematize over patch.** Fixes belong in tokens and shared styles, named by role.
- **Adapt, don't transplant.** Bringhurst's print rules sometimes need a screen translation (baseline grid → spacing scale; physical measure → `max-width`; the size scale → a token ramp). Translate; don't apply literally.
- **Respect the brand's own decisions.** Typeface choice belongs to the brand. Recommend the *characteristics* to look for (tabular figures, small caps, optical sizing, screen-hinted at small sizes) rather than dictating a specific face, unless asked.
- **Honor the content.** When a judgment call is close, choose the option that makes the content lead and the chrome recede.

## Examples

**Example 1 — casing**
Observed: every column header, field label, tab, and button is uppercase.
Finding: *Hierarchy collapsed.* Uppercase is emphasis; when everything is uppercase, nothing is emphasized and the eye has no guide — and the labels compete with the data they describe. Principle: hierarchy and casing; honoring content. Fix: reserve uppercase for one tier (section titles); set field labels and column headers in small caps; set buttons in sentence case, with weight and color carrying the emphasis.

**Example 2 — figures**
Observed: a table of prices and P&L with left-aligned numbers in proportional figures.
Finding: *Numbers don't scan.* Columns of figures can't be compared when digits don't stack. Principle: figures; rhythm and alignment. Fix: right-align (or decimal-align) numeric columns, set them in tabular lining figures (`font-variant-numeric: tabular-nums lining-nums`), and remove any letter-spacing from numerics. Right-align the header cell too, so it sits over its digits.

---

This skill's body also works as a standalone prompt: paste the sections from "The governing idea" through "Principles for the fixes" ahead of a typography task to get the same behavior without skill infrastructure.
