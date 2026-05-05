---
inclusion: manual
---

# BA Step — Status (Inspection)

Load khi chạy `ba-start status`.

## Memory Read Scope
- Must read: contract
- May read: `project_memory` header, `memory_index` (activation + freshness)
- Must NOT read: log (unless --audit), warm shards, cold

## Prerequisites
- Resolve slug + date. If ambiguous → stop and ask.

## Output Format
```
Project: {slug}
Date set: {date}

[Core]
- [x] PROJECT-HOME.md — 2026-03-26
- [x] 01_intake/intake.md — 2026-03-26
- [x] 02_backbone/backbone.md — 2026-03-26

[Module: auth-flow]
- [x] 03_modules/auth-flow/user-stories.md — 2026-03-26
- [ ] 03_modules/auth-flow/srs.md — missing
- [ ] 03_modules/auth-flow/wireframe-input.md — missing

[Compiled]
- [x] 04_compiled/compiled-frd.html — 2026-03-26
- [x] 04_compiled/compiled-srs.html — 2026-03-26

[Designs]
- [ ] designs/{slug}/DESIGN.md — missing
- [!] wireframe handoff — skipped — 2026-03-26
```

Rules:
- Print exists/missing + last-modified date
- For wireframe: print explicit state + marker date
- Print memory/activation/owner metadata from project_memory and memory_index
- For delegated slices: print tracker state, mark `likely stalled` when heartbeat exceeds stall_after_minutes
