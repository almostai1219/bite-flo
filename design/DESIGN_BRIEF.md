# Design Brief

Status: draft
Created: 2026-06-16

This brief is for visual redesign specification only. The immediate goal is to prepare accurate handoff documents for external design-generation tools such as Google Stitch or Claude Design. Do not start restyle implementation from this brief alone.

## Goal

Prepare a design handoff package for BiteFlo's Chrome Side Panel UI so external design-generation tools can propose visuals that fit the current product architecture.

Expected redesign order:

1. New token proposal: colors, type scale, spacing, radius, shadows.
2. Shared UI module styling: buttons, inputs, cards, status strips, nav, prompt cards.
3. Page-specific differences only after shared modules are stable.

## Product Surface

- Platform: Chrome Extension Side Panel.
- Primary UI file: `sidepanel.html`.
- Main UI script: `src/sidepanel.js`.
- Visible tabs:
  - Narrative Scan
  - AI Flows
  - Prompt Manager
  - Format Manager
  - Settings

## Hard Constraints

Confirmed from project docs:

- Chrome MV3 CSP must be preserved: no inline scripts or inline event handlers. See Decision 15.
- Side Panel is the primary UI and fixed to the browser side panel surface. See Decision 10.
- Visual redesign must not change workflow semantics, message contracts, or storage schema.
- Do not modify `START_EXTRACT`, `START_DISTILL`, `activeDistillContext`, or core message routing as part of visual work.
- `Narrative Scan` and `AI Flows` are distinct workflow product surfaces; share UI grammar first, not orchestration. See Decisions 58 and 59.
- `Narrative Scan` currently uses a two-stage manual-review-first workflow; do not hide manual recovery affordances.
- `AI Flows` remains the more general composition surface.
- Existing tabs and page responsibilities should remain intact unless a separate IA decision is made.
- All `<select>` controls should use `.select-compact`.
- `initETLTab()` timing must not be affected by design changes.

## Scope Draft

Recommended in scope:

- Token refresh for color, type, radius, spacing, and shadow.
- Shared UI module styling:
  - top navigation
  - workflow cards
  - status strips
  - buttons
  - inputs / textareas / selects
  - AI pills
  - prompt/schema cards
  - empty states
  - tooltips

Recommended out of scope:

- Workflow runner behavior.
- Message contract changes.
- Storage schema changes.
- Reordering or redefining workflow stages.
- Replacing Side Panel with popup, content overlay, or web app.
- Hiding manual capture/review paths.

## Screenshot Status

- Screenshot folder: `design/screenshots/`
- Screenshot checklist: `design/screenshots/README.md`
- Current screenshots: UNVERIFIED, not yet provided.

## Interview

### 1. Feeling

Question:
What should BiteFlo feel like? Please choose 3-5 adjectives.

Suggested answer:
Focused, calm, precise, research-grade, low-noise.

Reason:
BiteFlo is a browser-native narrative analysis tool. The UI should support long, careful work without feeling like a marketing page or playful consumer app.

Your answer:
Calm, precise, elegant, spacious.

### 2. Positive References

Question:
Which 2-3 apps or websites do you like visually, and what do you like about each?

Suggested answer:
Figma: detailed, clean, and highly organized. Tiffany: bright, comfortable to read, and elegant.

Your answer:
Figma — very detailed and clean, but still orderly.
Tiffany — bright overall, comfortable to read, and elegant.

### 3. Negative References

Question:
What should this absolutely not look like?

Suggested answer:
Do not look like Taobao or a crypto dashboard: too many colors and too much information competing at once.

Your answer:
Do not look like Taobao or crypto dashboards. They feel too crowded, with too much information and too many colors compressed together.

### 4. Hard Constraints Confirmation

Question:
Are the hard constraints above correct, or should any be added/removed?

Suggested answer:
Keep the current Chrome Side Panel architecture. Produce design specifications only; do not change IA, workflow order, runtime state, message contracts, or storage schema.

Your answer:
The goal is to generate specification documents that fit the current architecture, then use those documents in Google Stitch or Claude Design for more accurate visual generation.

### 5. Scope Confirmation

Question:
Should the redesign be pure visual layer only, or may it include small layout changes?

Suggested answer:
Specification-only for now. The design tools may propose token, component, and page-level visual directions, but implementation remains a separate later step.

Your answer:
Specification-only for now. No implementation or restyle in this step.

## Follow-up

- `design/` is ignored in Git so screenshots with personal data are not committed by default.
- Capture screenshots before asking for external visual redesign.
- Review `--shadow-soft`, which is referenced in CSS but not currently defined in the token set.
