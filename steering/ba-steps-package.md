---
inclusion: manual
---

# BA Step — Package (Step 12)

Load khi chạy `ba-start package`.

## Memory Read Scope
- Must read: contract
- May read: `project_memory` (compact, consistency check), `memory_index` (health overview)
- Must NOT read: log, cold, warm shards

## Prerequisites
- Require at least one emitted downstream artifact
- If engagement emitted module SRS → require at least one `paths.srs`
- If wireframe state = `missing` → print marker path + stop
- If `completed`/`skipped`/`not-applicable` → continue

## Outputs
- Packaged HTML under `paths.compiled_root`
- Delivery summary

## Step 12 — Package deliverables

Final packaging + quality pass:
- Validate existing artifact set (NOT full rebuild)
- Regenerate `compiled_frd` when FRD exists, `compiled_srs` when SRS exists
- Verify cross-references: backbone ↔ downstream artifacts
- When FRD + SRS exist: check cross-references against stories
- Verify user-story traceability across FR, UC, SCR
- Validate naming conventions + file structure
- Flag broken links or missing sections
- Produce delivery summary

## Step 12.1 — Generate packaged HTML
Aggregate and convert to HTML. Output: `compiled_frd`, `compiled_srs`.
When engagement doesn't include SRS → package only emitted artifacts.
Preserve wireframe image/link references in packaged HTML.
