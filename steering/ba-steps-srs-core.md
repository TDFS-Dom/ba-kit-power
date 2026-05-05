---
inclusion: manual
---

# BA Step — SRS Core (Steps 8-11 Router + Groups A/B/C)

Load khi chạy `ba-start srs`. This is the SRS router + core groups.

## Memory Read Scope
- Must read: contract, `paths.backbone`, `paths.stories`
- May read: `project_memory` or hot shards, module warm shard, `paths.frd`
- Must NOT read: log, cold, other module shards

## Governance Gate
- Skip for first-pass creation
- For reruns: verify write authority + approved impact run

## Prerequisites
- Require: `paths.backbone` + `paths.stories`. Missing → print path + stop.
- SRS preflight: read backbone, stories, optional FRD, plan

## Execution Order
```
Step 8   → SRS Core (this file: Groups A, B, C)
Step 8.1 → Build wireframe constraint pack (this file)
Step 8.2 → Design decisions (ba-steps-srs-wireframes.md)
Step 9   → Wireframe handoff (ba-steps-wireframes.md)
Step 10  → Final screen descriptions (ba-steps-srs-wireframes.md)
Step 10.1 + 11 → Assembly (ba-steps-srs-assembly.md)
```

## Mode Rules
- `lite`: don't run SRS unless user explicitly asks
- `hybrid`: selective coverage — complex flows, risky validations, integrations, screens affecting delivery
- `formal`: full SRS set

## Group A — Core
- Purpose and Scope
- Overall Description
- Functional Requirements table

## Group B — Behavioral
- Use Case Specifications
- Each UC links to user stories and screens
- Actor actions = same terminology as stories/FRD
- Every detailed UC includes Process Flow (BPMN/Mermaid) or Sequence Diagram

## Group C — Screen Contract Plus
- Screen Contract Plus table
- Screen Inventory

Screen Contract Plus must define per screen:
- Screen ID, Classification, Portal ID
- Access Role / Actor
- Nav Schema ID, Expected Active Menu Item
- Navigation Region Visible
- Breadcrumb / Back Behavior
- Global vs Local Navigation
- Entry/Exit conditions, Key actions, Required states

Rules:
- Same Portal ID → same Nav Schema ID (unless exception declared)
- Modal/drawer/dialog with own interaction logic = primary screen
- Expected Active Menu Item must map to portal navigation schema

## Step 8.1 — Build wireframe constraint pack

After Groups B+C complete, assemble `wireframe-input.md`:
- Artifact set info + app type
- Use case excerpts per screen
- Screen Contract Plus + Screen Inventory
- Portal snapshot + navigation schema
- Menu matching checklist
- Non-negotiable constraints
- Stop conditions

Save to `paths.wireframe_input`.
