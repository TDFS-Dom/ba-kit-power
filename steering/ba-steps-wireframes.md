---
inclusion: manual
---

# BA Step — Wireframes (Step 9 Standalone)

Load khi chạy `ba-start wireframes` hoặc từ SRS pipeline.

## Memory Read Scope
- Must read: contract, `paths.wireframe_input` (or fallback sources)
- May read: `project_memory` or `memory_hot_decisions`, `design_doc`, module warm shard
- Must NOT read: log, cold, other module shards

## Governance Gate
- Skip for first-pass creation
- For reruns: verify write authority + approved impact run

## Prerequisites
Resolve wireframe source in order:
1. `paths.wireframe_input`
2. Exact pair of `srs_group` b + c
3. `paths.srs` when UC + Screen Contract Plus already assembled there
If none exist → print all expected paths + stop.

## Outputs
- `paths.design_doc`
- `paths.wireframe_map`
- `paths.wireframe_state`

## Step 9.1 — Resolve wireframe input pack
Parse input pack → build handoff plan:
- Group related screens by flow/module/journey
- Treat modal/dialog/drawer with flow impact as primary screens
- Derive supporting frames from documented states/validation/feedback
- Verify each group has portal snapshot + menu schema + active-menu expectations

## Step 9.2 — Ask for or refresh DESIGN.md
Check if `paths.design_doc` exists → reuse or refresh.
Minimum decision set: reference direction, visual tone, color, typography, component feel, layout, portal nav schema, active/selected rule, breadcrumb/back, exceptions, anti-patterns.
Persist or refresh → stop if user declines.

## Step 9.3 — Wireframe handoff preference
- `lite`: skip unless critical
- `hybrid`: critical-screen constraints automatically
- `formal`: full approved screen set

If skip → persist state `skipped`. No UI screens → `not-applicable`. Cannot complete → `missing`.

## Step 9.4 — Build manual wireframe handoff pack + checklist
For each approved screen group:
1. Read UC excerpts, Screen Contract Plus, portal snapshots, Screen Inventory
2. Read DESIGN.md
3. Verify constraints match portal ownership, menu schema, active behavior
4. Stop if missing portal snapshot or nav schema
5. Expand `wireframe_input` with full constraint set
6. Persist `wireframe_map` as manual handoff checklist:
   - Which primary screens must be drawn
   - Which supporting states must exist
   - Which portal/nav schema each screen follows
   - Active-menu evidence requirements
   - Non-negotiable labels/actions/validation cues
7. State explicitly: BA-kit does NOT generate wireframe itself. User designs manually.

After complete → persist `wireframe_state` with `State: completed`.
