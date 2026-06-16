# CSS Token Map

Generated for design-prep on 2026-06-16.

Scope scanned:
- `sidepanel.html`
- `NAV_MAP.md` for UI surface context

This map is a handoff aid for visual redesign. It does not change runtime behavior.

## Token Sources

Primary tokens live in `sidepanel.html` under `:root` and theme overrides:

- Base theme: `:root`
- Dark theme alias: `:root[data-theme="nt-dark"]`
- Light editorial theme: `:root[data-theme="editorial-light"]`
- Light studio theme: `:root[data-theme="studio-light"]`
- Accessibility overlays: `body.contrast-bright`, `body.contrast-max`, `body.font-comfortable`, `body.font-large`

## Font Tokens

| Token | Value | Current role |
|---|---|---|
| `--font-ui` | `'Noto Sans TC', sans-serif` | Default UI font |
| `--font-mono` | `'DM Mono', monospace` | Labels, counters, code-like UI, compact metadata |
| `--font-editorial` | `Georgia, 'Times New Roman', 'Noto Serif TC', serif` | Editorial-light headings |

Notes:
- Hardcoded `DM Mono` declarations have been consolidated to `--font-mono`.
- Remaining hardcoded font family risk: multiple editor/input areas still use `'Noto Sans TC', sans-serif` directly instead of `--font-ui`.

## Spacing Tokens

| Token | Value |
|---|---|
| `--space-1` | `4px` |
| `--space-2` | `8px` |
| `--space-3` | `14px` |
| `--space-4` | `20px` |
| `--space-5` | `24px` |

Hardcode risk:
- Many local rules still use direct spacing values such as `6px`, `8px`, `10px`, `12px`, `14px`, `20px`, `24px`, and `40px`.
- These are mostly layout-specific and should not all be tokenized blindly. During redesign, start with shared elements: buttons, cards, nav, status strips, form controls.

## Radius Tokens

| Token | Value | Current role |
|---|---|---|
| `--radius-sm` | `5px` | Small controls |
| `--radius-md` | `8px` | Cards / panels via `--r2` |
| `--radius-lg` | `14px` | Larger rounded surfaces |
| `--r` | `var(--radius-sm)` | Legacy shorthand |
| `--r2` | `var(--radius-md)` | Legacy shorthand |

Hardcode risk:
- `999px` is used for pills and circular controls.
- `12px`, `10px`, `8px`, `6px`, `4px`, `3px`, and `2px` remain as direct values.
- Current design guidance prefers cards at 8px radius or less unless intentionally larger; review all `12px` card-like surfaces before restyling.

## Shadow Tokens

| Token | Theme | Value |
|---|---|---|
| `--shadow-card` | base / nt-dark | `0 8px 24px rgba(0,0,0,.22)` |
| `--shadow-card` | editorial-light | `0 4px 12px rgba(56, 45, 31, 0.08)` |
| `--shadow-card` | studio-light | `0 1px 2px rgba(33, 40, 49, 0.03)` |

Hardcode risk:
- Hover shadows still appear directly, e.g. section/card/button hover shadows.
- `--shadow-soft` appears referenced in CSS but is not defined in the current token set. This should be reviewed before a visual redesign.

## Core Color Tokens

### Base / `nt-dark`

| Token | Value |
|---|---|
| `--bg` | `#0b1020` |
| `--bg2` | `#11182a` |
| `--bg3` | `#171f33` |
| `--line` | `rgba(255,255,255,0.08)` |
| `--line2` | `rgba(255,255,255,0.14)` |
| `--text` | `#f3f6ff` |
| `--text2` | `#c7cede` |
| `--text3` | `#8f97ab` |
| `--accent` | `#8b5cf6` |
| `--accent-bg` | `rgba(139,92,246,0.12)` |
| `--green` | `#46b96b` |
| `--red` | `#ff6b6b` |
| `--amber` | `#f59e0b` |
| `--blue` | `#6ea8ff` |

### Editorial Light

| Token | Value |
|---|---|
| `--bg` | `#f6f2ec` |
| `--bg2` | `#fffdf9` |
| `--bg3` | `#f3ede6` |
| `--line` | `#d8cec0` |
| `--line2` | `#b9ab98` |
| `--text` | `#211c17` |
| `--text2` | `#5d5347` |
| `--text3` | `#8f816f` |
| `--accent` | `#1f2f42` |
| `--accent-bg` | `rgba(73,96,123,0.08)` |

### Studio Light

| Token | Value |
|---|---|
| `--bg` | `#f4f3f0` |
| `--bg2` | `#f1f1ee` |
| `--bg3` | `#eeeff1` |
| `--line` | `#dde1e6` |
| `--line2` | `#d0d6dd` |
| `--text` | `#1f252c` |
| `--text2` | `#4f5a66` |
| `--text3` | `#828c98` |
| `--accent` | `#314152` |
| `--accent-bg` | `#dfe7f1` |

## Semantic Aliases

| Token | Source |
|---|---|
| `--page-bg` | `var(--bg)` |
| `--panel-bg` | theme-specific |
| `--card-bg` | theme-specific |
| `--card-bg-soft` | theme-specific |
| `--border-subtle` | usually `var(--line)` |
| `--border-strong` | usually `var(--line2)` |
| `--text-primary` | `var(--text)` |
| `--text-secondary` | `var(--text2)` |
| `--text-muted` | `var(--text3)` |
| `--text-heading` | theme-specific |

Design note:
- Prefer changing semantic aliases for redesign rather than rewriting every component selector.

## Component Tokens

### Buttons

| Token group | Tokens |
|---|---|
| Default | `--btn-bg`, `--btn-border`, `--btn-text` |
| Hover | `--btn-hover-bg`, `--btn-hover-border`, `--btn-hover-text` |
| Primary | `--btn-primary-bg`, `--btn-primary-border`, `--btn-primary-text` |
| Primary hover | `--btn-primary-hover-bg`, `--btn-primary-hover-border`, `--btn-primary-hover-text` |

Hardcode risk:
- `btn-danger`, `btn-success`, and several local action buttons still use direct semantic colors or inline-sized padding.

### Inputs

| Token | Role |
|---|---|
| `--input-bg` | Textarea/input/select background |
| `--input-border` | Default border |
| `--input-border-focus` | Focus border |
| `--input-text` | Input text |
| `--input-placeholder` | Placeholder text |

### Pills

| Token group | Tokens |
|---|---|
| Default | `--pill-bg`, `--pill-border`, `--pill-text` |
| Hover | `--pill-hover-border`, `--pill-hover-text` |
| Active | `--pill-active-bg`, `--pill-active-border`, `--pill-active-text` |

### Workflow Steps

| Token group | Role |
|---|---|
| `--step-1` to `--step-6` | Step number base colors |
| `--workflow-step-gloss` | Shared step badge gloss |
| `--workflow-step-*-border` | Card/step active border colors |
| `--workflow-step-*-shadow` | Card active shadows |

### Workflow Status

| Token group | Role |
|---|---|
| `--status-idle-*` | Idle top status strip |
| `--status-waiting-*` | Waiting/running top status strip |
| `--status-success-*` | Success/done top status strip |
| `--status-error-*` | Error/stopped top status strip |

### Item Status

| Token | Role |
|---|---|
| `--item-running-border` | Running prompt item border |
| `--item-running-shadow` | Running prompt item glow |
| `--item-done-border` | Done prompt item border |
| `--item-error-border` | Error prompt item border |

## Hardcoded Value Risks

These are the main orphan risks to address before or during visual redesign:

- Direct family references to `'Noto Sans TC', sans-serif` in editor/input areas.
- Direct theme override colors under `editorial-light`, `studio-light`, and contrast modes.
- Direct amber warning colors such as `rgba(245, 158, 11, ...)`, `#f5c67a`, and `#ffd58a`.
- Direct run status colors: `#ff7b7b`, `#f3c56a`.
- Direct neutral overlays such as `rgba(255,255,255,0.04)`, `rgba(255,255,255,.06)`, `rgba(240,240,240,.06)`.
- Direct hover shadows for `.section`, `.pcard`, and `.btn`.
- Inline style attributes in HTML markup, especially row gaps and margins near settings actions.

## Suggested Redesign Order

1. Update root/theme tokens: color, typography, radius, shadow.
2. Update shared components: `.btn`, `.input`, `.select-compact`, `.cf-card`, `.extract-global-status`, `.ai-pill`, `.pcard`.
3. Only then tune page-specific surfaces: `Narrative Scan`, `AI Flows`, `Prompt Manager`, `Format Manager`, `Settings`.

## Verification Status

- Token inventory: derived from static scan.
- Runtime UI screenshots: UNVERIFIED.
- Theme parity across `nt-dark`, `editorial-light`, `studio-light`: UNVERIFIED.
