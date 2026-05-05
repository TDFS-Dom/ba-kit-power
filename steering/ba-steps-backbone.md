---
inclusion: manual
---

# BA Step — Backbone (Step 5)

Load khi chạy `ba-start backbone`.

## Memory Read Scope
- Must read: contract, `paths.intake`
- May read: `project_memory`, `memory_index` (nav only), `memory_hot_vocabulary`, `memory_hot_decisions`
- Must NOT read: log, cold, warm shards

## Governance Gate
- Skip for first-pass creation (backbone doesn't exist yet)
- For reruns: verify write authority + approved impact run
- After mutation: offer to file change into canonical memory

## Prerequisites
- Require `paths.intake`. If missing → print path + stop.
- Narrow preflight: read only intake + plan (when exists)

## Outputs
- `paths.project_home`
- `paths.backbone`
- `paths.project_memory`

## Step 5 — Build requirements backbone

Create using backbone template. Must contain:
- Scope lock summary
- Selected engagement mode (lite/hybrid/formal)
- Business goals and success metrics
- Actors and feature map
- System-level portal matrix (for UI-backed scope)
- FR/NFR draft inventory
- Preliminary story map
- UI/screen coverage assessment
- Artifact emission gates
- Assumptions, risks, open questions

After writing backbone:
- Initialize/refresh `project_memory` (anti-drift layer)
- Refresh `PROJECT-HOME.md` (dashboard)

Backbone rules:
- Primary authoring source after intake
- Don't draft FRD/stories/SRS from raw intake once backbone exists
- Lock portal ownership and route-group ownership here before module-level screen work
- Keep concise and decision-oriented
