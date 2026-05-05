---
inclusion: manual
---

# BA Step — SRS Wireframes (Steps 8.2, 9, 10)

Load sau `ba-steps-srs-core.md` khi cần design decisions + final screen descriptions.

## Step 8.2 — Capture design decisions → DESIGN.md

Before wireframe handoff, ask user to make/approve design decisions:
- Reference direction, visual tone, color, typography
- Component feel, layout/responsive priority
- Portal navigation schema per portal
- Active/selected menu rule
- Breadcrumb/back behavior
- Anti-patterns

If `paths.design_doc` exists → ask reuse or refresh.
If not → ask user → persist using DESIGN.md template.
Stop before Step 9 if decisions unresolved.

## Group D — Technical (conditional)
- NFR, Data flow diagrams, ERD, API specs, Constraints
- Produce only when integrations/NFR/data modelling justify it

## Step 9 — Prepare manual wireframe handoff
Run standalone wireframe workflow (see `ba-steps-wireframes.md`).

Mode defaults inside SRS pipeline:
- `lite`: skip unless user explicitly asks
- `hybrid`: critical-screen constraints first
- `formal`: full approved screen set

## Step 10 — Final screen descriptions (Group E)

After Step 9 resolves, expand from:
- Use Cases + Screen Contract Plus + wireframe artifacts

Rules:
- Do NOT redefine Portal ID, Nav Schema ID, or active/highlight behavior
- If IA/menu must change → route through `impact`

Screen field table format:
| Field Name | Field Type | Description |
|---|---|---|
| [Field] | [Type] | **Display Rules:** [...] |
| | | **Behaviour Rules:** [...] |
| | | **Validation Rules:** [...] |
| | | **Rule Codes:** [CR-xxx] |
| | | **Message Codes:** [MSG-xxx] |
