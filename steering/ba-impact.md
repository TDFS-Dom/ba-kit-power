---
inclusion: manual
---

# BA-kit — Change Impact Triage

Load file này khi requirement thay đổi hoặc user gửi correction statement.

## Purpose
Phân tích ảnh hưởng TRƯỚC KHI sửa artifact. Không mutate — chỉ analyze + recommend.

## Prerequisites
- Resolve slug + date
- Require `paths.intake`
- Read `paths.backbone` when exists
- Read relevant downstream artifacts only when they exist and are relevant

## Decision Rules

### Source of Truth Order
1. `backbone` (if exists)
2. `intake` (fallback)

### Change Classification

| Type | Meaning |
|---|---|
| `wording-only` | Typo, formatting, no semantic change |
| `clarification-only` | Adds detail without changing scope |
| `backbone-change` | Touches feature scope, FR/NFR, actors, portal, navigation |
| `scope-lock-change` | Touches goals, out-of-scope, success metrics |
| `ui-impact` | Affects screen inventory, states, navigation, active/highlight |

### Routing Rules

| Change touches... | Route to... |
|---|---|
| Goals, out-of-scope, success metrics | `intake` first |
| Feature scope, FR/NFR, actors, portal, navigation schema | `backbone` first |
| Story wording / acceptance detail (within backbone intent) | `stories` |
| UC flow, validation, error states, screen behavior | `srs` |
| Screen inventory, state variants, overlays, field interactions | `srs` + mark `ui-impact` → include `wireframes` after |

### Never
- Never recommend `package` as first remediation after real requirement change
- Never mutate artifacts during impact analysis

## Output Format

```
BA Impact Analysis

Project: {slug}
Date set: {date}
Change type: {classification}
Source of truth: {backbone | intake}

Affected artifacts:
- {path} — {reason}

Unaffected artifacts:
- {path}

Recommended path:
1. {exact command}
2. {exact command}

Questions (if any):
- {focused question}
```

## Impact Anchors

| Artifact | What to check |
|---|---|
| intake | Business problem, goals, out-of-scope, success metrics |
| backbone | Scope lock, feature map, FR/NFR, actors, portal matrix, story map, UI coverage, gates |
| FRD | Feature wording, workflows, business rules, integrations |
| stories | Story intent, acceptance criteria |
| SRS | Use cases, Screen Contract Plus, validation, screen inventory, final descriptions |
| wireframe artifacts | Constraint pack, DESIGN.md assumptions, handoff checklist, state |
