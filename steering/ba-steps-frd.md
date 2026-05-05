---
inclusion: manual
---

# BA Step — FRD (Step 6)

Load khi chạy `ba-start frd`.

## Memory Read Scope
- Must read: contract, `paths.backbone`, `paths.plan` (when exists)
- May read: `project_memory` or hot vocabulary+decisions shards
- Must NOT read: log, cold, warm, unrelated module shards

## Governance Gate
- Skip for first-pass creation
- For reruns: verify write authority + approved impact run
- After mutation: offer to file change into canonical memory

## Prerequisites
- Require `paths.backbone`. Missing → print path + stop.
- Narrow preflight: read only backbone + plan

## Output
- `paths.frd`

## Step 6 — Produce FRD

From backbone using FRD template:
- Functional overview
- User personas
- Feature list with MoSCoW priorities
- Workflows (Mermaid)
- Data requirements
- Business rules
- Integration points
- Acceptance criteria

Mode rules:
- `hybrid`: concise, focused on features/workflows/business rules/integrations
- `lite`: emit only when user explicitly asks
- `formal`: full FRD

Save to `paths.frd`.
