# Design Generation Spec

Status: draft
Created: 2026-06-16

Use this document as the primary handoff prompt/spec for Google Stitch, Claude Design, or another external visual design generator.

The goal is not to redesign BiteFlo from scratch. The goal is to generate visual concepts that respect the current Chrome Extension Side Panel architecture, workflow semantics, and existing UI responsibilities.

## Files To Provide To The Design Tool

Provide these files together:

- `design/DESIGN_GENERATION_SPEC.md` — this file; primary generator instructions.
- `design/DESIGN_BRIEF.md` — product mood, references, constraints, and scope.
- `design/CSS_TOKEN_MAP.md` — current token inventory and hardcoded-value risks.
- `NAV_MAP.md` — current page/tab/component map and workflow boundaries.
- `design/screenshots/` — screenshots when available. If screenshots are missing, treat all visual assumptions as UNVERIFIED.

Optional context:

- `decisions.md` — architecture decisions. Do not contradict it.

## Product Summary

BiteFlo is a compact Chrome Extension Side Panel for browser-native narrative scanning, AI workflow handoff, prompt management, format/schema management, and local capture/export.

It should feel:

- Calm
- Precise
- Elegant
- Spacious

Positive references:

- Figma: detailed, clean, highly organized.
- Tiffany: bright, comfortable to read, elegant.

Negative references:

- Do not look like Taobao.
- Do not look like crypto dashboards.
- Avoid overloaded colors, crowded panels, dense visual noise, and many competing callouts.

## Non-Negotiable Architecture Boundaries

The generated design must preserve these boundaries:

- Platform remains a Chrome Extension Side Panel.
- Do not redesign it as a landing page, website, popup, content overlay, or mobile app.
- Keep the current top-level tabs:
  - Narrative Scan
  - AI Flows
  - Prompt Manager
  - Format Manager
  - Settings
- Do not change IA, page responsibility, workflow order, runtime state, storage schema, or message contracts.
- Do not remove manual recovery/capture paths.
- Do not hide the fact that Narrative Scan is a staged workflow.
- Do not combine Narrative Scan and AI Flows into one generic workflow.
- Do not introduce inline scripts or inline event handlers; Chrome MV3 CSP must remain compatible.
- Do not modify or reinterpret these runtime contracts:
  - `START_EXTRACT`
  - `START_DISTILL`
  - `activeDistillContext`

## Design Scope

In scope for generated output:

- A refreshed token proposal:
  - color palette
  - typography scale
  - spacing scale
  - radius scale
  - shadow/elevation rules
- Shared component styling:
  - top navigation
  - workflow cards
  - status strips
  - buttons
  - inputs, textareas, selects
  - AI pills
  - prompt/schema cards
  - empty states
  - compact tooltips
- Page-specific visual refinements after shared components are defined.

Out of scope:

- Workflow behavior.
- Message routing.
- Storage schema.
- Automation semantics.
- Background/content-script behavior.
- Renaming runtime concepts.
- Removing visible manual review, capture, or save affordances.

## Required Output From Design Tool

Ask the design tool to produce output in this order:

1. Token proposal.
2. Shared component style guide.
3. Page-by-page visual notes.
4. Implementation notes mapped to existing selectors/classes/tokens when possible.

The design tool should not start by drawing unrelated screens. It should first propose a token system that can be applied to the existing UI.

## Current UI Surfaces

### Narrative Scan

Purpose:

- A guided two-stage workflow for X/Grok-first narrative extraction and later output formatting.

Important visual expectations:

- Clear staged progression.
- Calm status strip at the top.
- Four workflow cards:
  - Extract Setup
  - Extract Review
  - Output Setup
  - Capture & Save
- Stage 2 must visually feel locked or unavailable until Stage 1 draft is confirmed.
- Manual paste/capture/save paths should feel intentional, not like error states.

### AI Flows

Purpose:

- A general composable AI workflow surface.

Important visual expectations:

- Similar workflow grammar to Narrative Scan, but not identical product semantics.
- Collapsible block cards.
- Top global status strip.
- Execute and Review areas should support manual capture and local save.
- Avoid making logs visually dominant.

### Prompt Manager

Purpose:

- Manage prompt series and reusable prompt cards.

Important visual expectations:

- Dense but orderly.
- Expandable cards.
- One clear editing focus at a time.
- Autosave should feel quiet and trustworthy.

### Format Manager

Purpose:

- Manage schema/format templates.

Important visual expectations:

- Same card language as Prompt Manager.
- Slightly more technical/editorial feel is acceptable.
- Long text editing must remain comfortable.

### Settings

Purpose:

- Automation, folders, theme, font, contrast, and local preferences.

Important visual expectations:

- Simple preference groups.
- No marketing language.
- Controls should be readable and predictable.

## Visual Direction

Aim for a bright, precise, low-noise professional tool. The current app has dark and light theme support; generated concepts may propose a new primary direction, but should explain how the system maps across themes.

Preferred qualities:

- Bright enough to read comfortably for long sessions.
- Elegant without being decorative.
- Structured like a tool for careful work.
- Clear hierarchy through spacing, borders, type, and subtle surface changes.
- Semantic color only when it communicates state.

Avoid:

- Loud gradients.
- Many saturated colors competing at once.
- Marketing hero sections.
- Decorative background blobs.
- Oversized rounded cards.
- Card-within-card compositions.
- Crypto dashboard density.
- Shopping-site visual overload.

## Token Guidance

Use `CSS_TOKEN_MAP.md` as the source for current token names. Prefer proposing changes through semantic tokens rather than page-specific one-off colors.

Start from these groups:

- Core surfaces: `--bg`, `--bg2`, `--bg3`
- Borders: `--line`, `--line2`
- Text: `--text`, `--text2`, `--text3`
- Semantic states: `--green`, `--red`, `--amber`, `--blue`
- Component aliases:
  - button tokens
  - input tokens
  - pill tokens
  - workflow step tokens
  - workflow status tokens
  - item status tokens

Important token risks to address:

- `--shadow-soft` is referenced but not defined.
- Some warning/status colors are still hardcoded.
- Some font declarations still directly use font-family values instead of tokens.
- Some spacing/radius values are local layout values and should not all be tokenized blindly.

## Component Rules

### Navigation

- Keep top navigation compact.
- It must work in a narrow side panel.
- Do not turn navigation into a landing-page header.

### Cards

- Cards represent work areas, not marketing content.
- Use restrained radius.
- Avoid nested cards unless a repeated item genuinely needs its own boundary.
- Workflow cards should have clear headers, status affordances, and compact controls.

### Buttons

- Keep buttons compact and action-oriented.
- Primary actions should be obvious but not oversized.
- Destructive actions should be visually distinct but not alarming until hovered or confirmed.

### Inputs And Editors

- Long prompt/schema/result text must be comfortable to read and edit.
- Use sufficient line height.
- Preserve focus states.
- Avoid tiny text in editable long-form areas.

### Status

- Status should be calm and scannable.
- Use semantic colors sparingly:
  - waiting/running
  - success
  - error
  - idle
- Do not make status strips look like ad banners.

## Screenshot Handling

Screenshots are the only reliable visual source for current state. Until screenshots are provided, all generated page-specific visual assumptions must be marked UNVERIFIED.

Expected screenshot folder:

- `design/screenshots/`

Expected widths:

- Narrow side panel: approximately 360-420px.
- Wide side panel: approximately 700-900px.

## Final Design Tool Prompt

Use this prompt when pasting the document set into a design generator:

```text
Design a visual refresh specification for BiteFlo, a Chrome Extension Side Panel workflow tool.

Respect the existing architecture and tabs. Do not redesign the product flow, IA, runtime behavior, message contracts, or storage schema. Generate a visual direction that can be implemented by changing CSS tokens and shared component styles first, then page-specific styles only where necessary.

Desired feel: calm, precise, elegant, spacious. Positive references: Figma for clean organization; Tiffany for brightness, reading comfort, and elegance. Avoid Taobao or crypto-dashboard density: no overloaded colors, crowded panels, or competing visual noise.

Please output:
1. Token proposal.
2. Shared component style guide.
3. Page-by-page visual notes for Narrative Scan, AI Flows, Prompt Manager, Format Manager, and Settings.
4. Implementation notes that map back to existing token groups and selectors when possible.

Mark any page-specific assumptions as UNVERIFIED if screenshots are not provided.
```
