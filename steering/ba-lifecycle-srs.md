---
inclusion: manual
---

# BA Lifecycle — SRS

> **⚠️ DEPRECATED:** Prefer `ba-steps-srs-core.md` + `ba-steps-srs-wireframes.md` + `ba-steps-srs-assembly.md` which contain the full step logic. This file is kept for backward compatibility only.

Load file này khi produce Software Requirements Specification (Steps 8-11).

## Prerequisites
- `paths.backbone` + `paths.stories` must exist
- Module must be resolved
- If missing → print path + command to run, stop

## Execution Order

```
Step 8   → SRS Core (Groups A, B, C)
Step 8.1 → Build wireframe constraint pack
Step 8.2 → Capture design decisions → DESIGN.md
Step 9   → Wireframe handoff (see ba-lifecycle-wireframes.md)
Step 10  → Final screen descriptions (Group E)
Step 10.1 → Validation pack (Group F)
Step 11  → Assembly + quality review
```

## Step 8 — SRS Core

### Group A — Core
- Purpose and Scope
- Overall Description
- Functional Requirements table

### Group B — Behavioral
- Use Case Specifications
- Each UC links to user stories and screens
- Actor actions use same terminology as stories/FRD
- Every detailed UC includes Process Flow (BPMN/Mermaid) or Sequence Diagram

### Group C — Screen Contract Plus
- Screen Contract Plus table
- Screen Inventory

Screen Contract Plus must define per screen:
- Screen ID, Classification, Portal ID
- Access Role / Actor
- Nav Schema ID, Expected Active Menu Item
- Navigation Region Visible
- Breadcrumb / Back Behavior
- Global vs Local Navigation
- Entry/Exit conditions
- Key actions, Required states

Rules:
- Same Portal ID → same Nav Schema ID (unless exception declared)
- Modal/drawer/dialog with own interaction logic = primary screen
- Expected Active Menu Item must map to portal navigation schema

## Step 8.1 — Wireframe Constraint Pack

After Groups B+C complete, assemble `wireframe-input.md`:
- Artifact set info + app type
- Use case excerpts per screen
- Screen Contract Plus
- Screen Inventory
- Portal snapshot + navigation schema
- Menu matching checklist
- Non-negotiable constraints
- Stop conditions

Save to `plans/{slug}-{date}/03_modules/{module_slug}/wireframe-input.md`

## Step 8.2 — Design Decisions

Before wireframe handoff, capture/confirm design decisions:
- Reference direction, visual tone, color, typography
- Component feel, layout/responsive priority
- Portal navigation schema per portal
- Active/selected menu rule
- Breadcrumb/back behavior
- Anti-patterns

If `designs/{slug}/DESIGN.md` exists → ask reuse or refresh.
If not → ask user for decisions → persist.

## Group D — Technical (conditional)
- NFR, Data flow diagrams, ERD, API specs, Constraints
- Produce only when integrations/NFR/data modelling justify it

## Step 10 — Final Screen Descriptions (Group E)

After wireframe handoff resolves:
- Expand from Use Cases + Screen Contract Plus + wireframe artifacts
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

## Step 10.1 — Validation Pack (Group F)
- Test Cases
- Glossary
- Traceability cross-references

## Step 11 — Assembly

Assembly procedure (INLINE, never delegate):
1. Write SRS skeleton to `paths.srs`
2. For each group (A→B→C→D→E→F): read fragment → edit-append into skeleton
3. Cross-artifact consistency check:
   - UC steps ↔ screen fields/actions
   - Screen Contract Plus ↔ wireframe constraints ↔ final descriptions
   - UC actor actions = screen User Actions (same wording)
   - UC system responses = screen Behaviour Rules
   - Alternate flows reflected in screen error states
   - Story AC covered by UC postconditions + screen validation
4. Resolve placeholder references
5. Verify every SCR and UC traces to user stories
6. Delete group fragments after verified merge

## Shared Rules for SRS

### Rule Codes
Format: `CR-{TYPE}-{NN}` where TYPE = DIS, BEH, VAL, or MIX

### Message Codes
Format: `MSG-{TYPE}-{NN}` where TYPE = ERR, WRN, SUC, or INF

### Centralization
- Reusable cross-screen rules → Common Rules section, referenced by code
- Reusable messages → Message List section, referenced by code
- Do NOT duplicate rules/messages verbatim across screens
