---
inclusion: always
---

# BA-kit Contract

Core contract cho BA-kit Power. Load file này TRƯỚC mọi steering file khác.

## Defaults

- Language: `vi` (Vietnamese)
- Date token format: `YYMMDD-HHmm`
- Mode: `hybrid`
- UI baseline: `Shadcn UI`

## Paths

```yaml
project_root: plans/{slug}-{date}
project_home: plans/{slug}-{date}/PROJECT-HOME.md
intake: plans/{slug}-{date}/01_intake/intake.md
plan: plans/{slug}-{date}/01_intake/plan.md
backbone: plans/{slug}-{date}/02_backbone/backbone.md
project_memory: plans/{slug}-{date}/02_backbone/project-memory.md
module_root: plans/{slug}-{date}/03_modules/{module_slug}
frd: plans/{slug}-{date}/03_modules/{module_slug}/frd.md
stories: plans/{slug}-{date}/03_modules/{module_slug}/user-stories.md
srs: plans/{slug}-{date}/03_modules/{module_slug}/srs.md
wireframe_input: plans/{slug}-{date}/03_modules/{module_slug}/wireframe-input.md
wireframe_map: plans/{slug}-{date}/03_modules/{module_slug}/wireframe-map.md
wireframe_state: plans/{slug}-{date}/03_modules/{module_slug}/wireframe-state.md
design_doc: designs/{slug}/DESIGN.md
compiled_root: plans/{slug}-{date}/04_compiled
compiled_frd: plans/{slug}-{date}/04_compiled/compiled-frd.html
compiled_srs: plans/{slug}-{date}/04_compiled/compiled-srs.html
collab_home: plans/{slug}-{date}/COLLAB-HOME.md
module_home: plans/{slug}-{date}/03_modules/{module_slug}/MODULE-HOME.md
```

## Commands & Prerequisites

| Command | Module Required | Requires | Outputs |
|---|---|---|---|
| intake | No | raw input | project_home, intake, plan |
| backbone | No | intake | project_home, backbone, project_memory |
| frd | Yes | backbone | frd |
| stories | Yes | backbone | stories |
| srs | Yes | backbone, stories | srs, wireframe_input |
| wireframes | Yes | wireframe_input | design_doc, wireframe_map, wireframe_state |
| package | No | at least one downstream artifact | compiled_frd, compiled_srs |
| impact | No | intake | (analysis only, no mutation) |
| status | No | — | (inspection only) |

## Resolution Rules

### Slug
1. Prefer explicit `--slug`
2. Otherwise inspect directories matching `{slug}-{YYMMDD-HHmm}` under `plans/`
3. If more than one slug exists → stop and ask

### Date
1. Prefer explicit `--date`
2. Otherwise derive from resolved project directory name
3. If ambiguous → stop and ask

### Module
1. For module-required commands, prefer explicit `--module`
2. If exactly one module directory exists → use it
3. If multiple → stop and ask
4. Never infer from partial filename matches

## Behavior Rules

### Fail-Closed
- Never silently choose slug, date, or module by mtime
- Never use broad `*-{slug}*` matching when exact paths exist
- If prerequisite missing → print exact path + command to run, then stop
- If ambiguous → stop and ask instead of guessing

### Overwrite Protection
Before mutating backbone, frd, stories, srs, wireframes, or package:
1. Check if target output path exists
2. If exists → print path and ask whether to overwrite
3. If no explicit approval → stop

### Impact-First Rule
- Never mutate artifacts from a bare correction statement
- Route through `impact` first unless edit is obviously wording-only
- A short correction like "Không có nhóm admin user" = impact input

### Execution Lock
After user approves a mutating rerun step:
- Keep that step locked for the rest of the run
- Do not reopen generic discovery
- Only break lock when command/slug/date/module becomes genuinely ambiguous

### Large Artifact Write Protocol
When generating artifacts >150 lines:
1. Write skeleton first (headings, boilerplate)
2. Append group content sequentially (one epic/UC at a time)
3. Never assemble full artifact in memory then flush

### Source of Truth Order
1. `backbone` (primary after scope lock)
2. `intake` (fallback)

### Next Step Order
`intake → backbone → frd → stories → srs → wireframes → package → status`

## Wireframe States
- `completed` — handoff pack ready
- `skipped` — user chose to skip
- `not-applicable` — no UI-backed screens
- `missing` — expected but not done (blocks package)

## Engagement Modes

| Mode | Default Artifacts | When |
|---|---|---|
| lite | intake + backbone + stories | Simple, low-risk |
| hybrid | intake + backbone + stories + targeted FRD/SRS | Default for solo IT BA |
| formal | Full artifact suite | Governance, vendor handoff, regulatory |

## Project Memory
- Compact mode: single `project-memory.md` file
- Contains: canonical vocabulary, approved decisions, assumptions, corrections, push-back triggers
- Runtime-neutral: works across any IDE
- Not source of truth — backbone is
