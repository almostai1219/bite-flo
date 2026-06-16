# Screenshot Checklist

Store screenshots in this folder using:

`<page>-<component-or-state>-<breakpoint>.png`

Examples:
- `narrative-scan-idle-narrow.png`
- `ai-flows-review-filled-wide.png`
- `prompt-manager-import-open-narrow.png`

Privacy note:
- Screenshots are ignored by default via `.gitignore`; keep generated screenshots local unless there is an explicit reason to commit sanitized examples.
- Current screenshots are UNVERIFIED because no image files have been provided yet.

## Breakpoints

Because BiteFlo is a Chrome Side Panel, capture two Side Panel widths rather than mobile/desktop pages:

- `narrow`: approximately 360-420px Side Panel width.
- `wide`: approximately 700-900px Side Panel width.

## Required Screenshots

### Narrative Scan

- `narrative-scan-idle-narrow.png` — initial state with global status strip.
- `narrative-scan-idle-wide.png`
- `narrative-scan-prompt-expanded-narrow.png` — Card 01 prompt editor expanded.
- `narrative-scan-prompt-expanded-wide.png`
- `narrative-scan-grok-inline-warning-narrow.png` — Inline X Panel selected.
- `narrative-scan-stage1-running-narrow.png` — after sending, status waiting/running if possible.
- `narrative-scan-extract-review-filled-narrow.png` — Stage 1 draft textarea filled.
- `narrative-scan-phase2-unlocked-narrow.png` — Output Setup unlocked.
- `narrative-scan-capture-save-filled-narrow.png` — final output textarea filled.

### AI Flows

- `ai-flows-idle-narrow.png` — empty/default preset state.
- `ai-flows-idle-wide.png`
- `ai-flows-source-filled-narrow.png` — source textarea with captured/pasted text.
- `ai-flows-task-selected-narrow.png` — prompt selected and preview/editor visible.
- `ai-flows-format-selected-narrow.png` — schema selected and preview visible.
- `ai-flows-grok-inline-selected-narrow.png`
- `ai-flows-execute-running-narrow.png` — run status visible if possible.
- `ai-flows-review-empty-narrow.png`
- `ai-flows-review-filled-narrow.png`

### Prompt Manager

- `prompt-manager-empty-narrow.png` — if empty state is reachable.
- `prompt-manager-filled-narrow.png` — typical starter pack / real data state.
- `prompt-manager-card-expanded-narrow.png`
- `prompt-manager-add-prompt-open-narrow.png`
- `prompt-manager-new-series-open-narrow.png`
- `prompt-manager-edit-series-open-narrow.png`
- `prompt-manager-import-filepicker-narrow.png` — if OS/browser file picker can be captured safely; otherwise mark UNVERIFIED.

### Format Manager

- `format-manager-empty-narrow.png` — if empty state is reachable.
- `format-manager-filled-narrow.png`
- `format-manager-card-expanded-narrow.png`
- `format-manager-add-schema-open-narrow.png`
- `format-manager-import-filepicker-narrow.png` — if capturable; otherwise mark UNVERIFIED.

### Settings

- `settings-default-narrow.png`
- `settings-theme-menu-open-narrow.png`
- `settings-font-large-narrow.png`
- `settings-contrast-max-narrow.png`

### Global / Shared UI

- `topnav-language-menu-open-narrow.png`
- `workflow-tooltip-open-narrow.png`
- `status-strip-idle-narrow.png`
- `status-strip-waiting-narrow.png`
- `status-strip-success-narrow.png`
- `status-strip-error-narrow.png`

## Optional Theme Coverage

Repeat core screens for each theme if the redesign will preserve all current themes:

- `nt-dark`
- `editorial-light`
- `studio-light`

Example:
- `narrative-scan-idle-nt-dark-narrow.png`
- `narrative-scan-idle-editorial-light-narrow.png`
- `narrative-scan-idle-studio-light-narrow.png`
