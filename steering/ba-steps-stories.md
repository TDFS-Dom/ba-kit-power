---
inclusion: manual
---

# BA Step — User Stories (Step 7)

Load khi chạy `ba-start stories`.

## Memory Read Scope
- Must read: contract, `paths.backbone`
- May read: `paths.plan`, `paths.frd` (when exists), `project_memory` or hot shards
- Must NOT read: log, cold, warm, unrelated module shards

## Governance Gate
- Skip for first-pass creation
- For reruns: verify write authority + approved impact run
- After mutation: offer to file change into canonical memory

## Prerequisites
- Require `paths.backbone`. Missing → print path + stop.
- Narrow preflight: read backbone, plan (when adds context), frd (when exists)

## Output
- `paths.stories`

## Step 7 — Produce user stories

From backbone feature map + FR draft using user story template:
- Epic and feature breakdown
- User stories with acceptance criteria (Given/When/Then)
- INVEST validation
- Story-to-screen alignment when UI exists

Save to `paths.stories`.
