---
inclusion: manual
---

# BA Lifecycle — Wireframe Handoff

> **⚠️ DEPRECATED:** Prefer `ba-steps-wireframes.md` which contains the full step logic. This file is kept for backward compatibility only.

Load file này khi prepare manual wireframe handoff pack (Step 9).

## Prerequisites
- Wireframe input pack (`wireframe-input.md`) or fallback sources must exist
- Fallback resolution order:
  1. `paths.wireframe_input`
  2. SRS groups B + C
  3. Full SRS with UC + Screen Contract Plus sections
- If none exist → print all expected paths + stop

## Outputs
- `designs/{slug}/DESIGN.md`
- `plans/{slug}-{date}/03_modules/{module_slug}/wireframe-map.md`
- `plans/{slug}-{date}/03_modules/{module_slug}/wireframe-state.md`

## Step 9.1 — Resolve Wireframe Input Pack

Parse input pack to build handoff plan:
- Group related screens by flow/module/journey
- Treat modal/dialog/drawer overlays with flow impact as primary screens
- Derive supporting frames from documented states, validation rules, feedback surfaces
- Verify each screen group has portal snapshot + menu schema + active-menu expectations

## Step 9.2 — Runtime DESIGN.md

Check if `designs/{slug}/DESIGN.md` exists:
- If exists → ask reuse or refresh
- If not → ask user for design decisions

Minimum decision set:
- Reference direction / inspiration
- Visual tone + density
- Color direction + contrast
- Typography direction
- Component feel
- Layout / responsive priority
- Portal navigation schema per portal
- Active/selected menu rule
- Breadcrumb / back behavior
- Hidden/contextual nav exceptions
- Anti-patterns

DESIGN.md template structure:
```markdown
# DESIGN.md - [Project Name]

## 0. Scope Of Use
## 1. Visual Theme & Atmosphere
## 2. Information Architecture (Portals & Navigation)
### 2.1 Portal Summary
### 2.2 Navigation Schema
## 3. Color Palette & Roles
## 4. Typography Rules
## 5. Component Stylings
## 6. Layout Principles
## 7. Depth & Elevation
## 8. Do's and Don'ts
## 9. Responsive Behavior
## 10. Design Handoff Guide
```

## Step 9.3 — Wireframe Handoff Preference

Mode defaults:
- `lite`: skip unless screen explicitly marked critical
- `hybrid`: prepare critical-screen constraints automatically
- `formal`: prepare full approved screen set

If user skips → persist state `skipped`
If no UI screens → persist state `not-applicable`
If cannot complete → persist state `missing` + report failure

## Step 9.4 — Build Handoff Pack + Checklist

For each approved screen group:
1. Read UC excerpts + Screen Contract Plus + portal snapshots
2. Read DESIGN.md
3. Verify constraints match portal ownership, menu schema, active/highlight behavior
4. Stop if portal snapshot or navigation schema missing
5. Expand wireframe-input.md with full constraint set
6. Persist wireframe-map.md as manual handoff checklist:
   - Which primary screens must be drawn
   - Which supporting states must exist
   - Which portal/nav schema each screen follows
   - Which screens show active-menu evidence
   - Where to attach result in final document
   - Non-negotiable labels, actions, validation cues

## wireframe-map.md Template

```markdown
# Wireframe Handoff Map

## Handoff Checklist

| Screen ID | Screen Name | Portal | Nav Schema | Active Menu | Must Draw | Attach Location |
|---|---|---|---|---|---|---|
| SCR-01 | [Name] | [Portal] | [NAV-xx] | [Item] | Primary | SRS § Screen Descriptions |

## Supporting States Required

| Parent Screen | State | Purpose | Must Show |
|---|---|---|---|
| SCR-01 | Empty | No data | Empty illustration + CTA |
| SCR-01 | Error | API failure | Error banner + retry |
| SCR-01 | Loading | Initial load | Skeleton screen |

## Non-Negotiable Constraints

| Screen ID | Labels/Actions | States | Navigation | Validation |
|---|---|---|---|---|
| SCR-01 | [Submit, Cancel] | [Loading, Empty, Error] | [Header + active menu] | [Inline error + toast] |
```

## Key Rules
- BA-kit does NOT generate wireframes — user designs manually or with external tool
- User manually inserts mockup reference into final SRS
- Every global nav screen must show correct active/selected state
- If screen hides global nav → document exception explicitly
- Use Shadcn UI as fallback baseline only when DESIGN.md leaves detail unspecified
