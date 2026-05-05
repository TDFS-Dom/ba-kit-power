---
inclusion: manual
---

# BA Lifecycle — Package

> **⚠️ DEPRECATED:** Prefer `ba-steps-package.md` which contains the full step logic. This file is kept for backward compatibility only.

Load file này khi xuất gói bàn giao HTML (Step 12).

## Prerequisites
- At least one emitted downstream artifact for the selected mode
- If wireframe state is `missing` → print marker path + stop
- If `completed`, `skipped`, or `not-applicable` → continue

## Step 12 — Package Deliverables

### Validation Pass
- Verify all deliverables follow templates
- Check cross-references: backbone ↔ downstream artifacts
- When FRD + SRS exist: check cross-references against stories
- Verify user-story traceability across FR, UC, SCR
- Validate naming conventions and file structure
- Flag broken links or missing sections

### Cross-Artifact Consistency Check
- FRD features covered by user stories and SRS requirements
- Every SRS FR, UC, SCR maps to at least one user story
- UC actor actions match screen User Actions
- UC system responses match screen Behaviour Rules
- Screen Contract Plus entries match wireframe constraints + final descriptions
- Field names identical across UC steps, screen field tables, wireframe labels
- Story AC reflected in UC postconditions + screen Validation Rules

### HTML Generation
- Convert markdown artifacts to HTML for stakeholder review
- Output to `plans/{slug}-{date}/04_compiled/`
- Preserve Mermaid diagrams (rendered in-browser)
- Preserve wireframe images/links from markdown source
- Default: editable HTML (stakeholder can edit in browser)

### Delivery Summary
Produce summary noting:
- Artifacts packaged
- Quality issues found/resolved
- Residual issues flagged
- Wireframe handoff state
- Traceability coverage

## Rules
- Package is validation + compile, NOT full rebuild
- Do not rebuild intake/backbone/stories/SRS drafts
- Keep markdown as source of truth
- HTML is the stakeholder-facing copy
- Narrow scope: regenerate only target HTML, not entire compiled set
