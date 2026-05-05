---
inclusion: manual
---

# BA-kit Contract Behavior

Canonical LLM policy layer. Load cùng `ba-contract-data.md` khi cần full contract.

## Required Read Order
1. `ba-contract-data.md` for exact values
2. Selected BA workflow or skill stub
3. Only the step file(s) needed for the active command
4. Templates/upstream artifacts only when the active step needs them

## Shared Operating Rules
- Vietnamese by default unless user requests English
- Backbone = primary authoring source once it exists
- Exact artifact matching only. Never infer from "closest looking" filenames
- Never silently choose slug, date, or module by mtime
- `PROJECT-HOME.md` = navigation dashboard, NOT source of truth

## Argument Parsing
Parse tokens left to right: `--slug`, `--date`, `--module`, `--mode`. First remaining lifecycle token = subcommand. Friendly aliases: "continue/resume" → `next`, "đánh giá thay đổi" → `impact`, "chuẩn bị handoff UI" → `wireframes`, "xuất gói bàn giao" → `package`.

## Natural-Language Routing
Infer `impact` when: user refers to existing project + says requirement/rule/scope changed + not obviously wording-only. Bare correction statement = `impact`. Collaboration intent (PR/commit/merge) = `ba-collab` with explicit approval gate.

## Resolution Rules
- **Slug:** explicit → inspect directories → ambiguous = stop and ask
- **Date:** explicit → derive from directory name → ambiguous = stop and ask
- **Module:** explicit → single module = use it → multiple = stop and ask

## Prerequisite Behavior
Use `commands.<name>.requires` + `paths.*`. Missing prerequisite → print exact path + command to run, stop. For `package`: block only when wireframe state = `missing`.

## Overwrite Behavior
Before mutating backbone/frd/stories/srs/wireframes/package: check if exists → print path → ask approval → stop if no approval.

## Context-Loss Recovery
Reconstruct active target from resolved command + slug + date + module + on-disk artifacts. Continue from next unresolved step.

## Accepted-Scope Execution Lock
After user approves a mutating rerun: keep step locked, don't reopen discovery, don't ask "what next?". Break lock only on genuine ambiguity.

## Delegation Contract
Narrow handoff packets only. Trackers under `paths.delegation_root`. Heartbeat every 5 min. Stall after 10 min. If packet too large → repartition before delegating.

## Large Artifact Write Protocol
Artifacts >150 lines → incremental writes:
1. Write skeleton first (headings, boilerplate)
2. Append group content sequentially (one epic/UC at a time)
3. Never assemble full artifact in memory then flush

## Granular Artifact Intervention
Minimum intervention units: goal/metric IDs, actor IDs, feature IDs, FR/NFR IDs, story IDs + AC, UC IDs + step rows, screen IDs, rule codes, message codes, glossary terms. Update only the narrowest source-of-truth artifact.

## Active Push-back & Fail-Closed
Material uncertainty → stop and ask. Includes: ambiguous scope/actor/module, conflicting terminology, unclear validation/error handling, unclear portal/nav ownership. Missing fact → mark as assumption. Downstream needs upstream decision → stop and route back.

## Project Memory Contract
- Initialize from latest accepted intake/backbone decisions
- Keep concise: vocabulary, decisions, assumptions, corrections, push-back triggers
- Not source of truth — backbone is
- Compact mode (single file) or Shard mode (directory tree)

## Memory Architecture
- `backbone.md` = primary scope truth
- `project-memory.md` = anti-drift support (compact)
- `project-memory/` = structured extension (complex projects)
- Index = bounded navigator, not monolith
- Log = optional append-only, excluded from default reads
- Cold = never loaded by default

## Activation Contract
Levels: Base → Modular → Program. Auto-escalation allowed, auto-downgrade not. Freeze fallback on mismatch.

## Read Scope Per Command
| Command | Must Read | Must NOT Read |
|---|---|---|
| intake | contract | memory shards, log, cold |
| backbone | contract, intake | log, cold, warm |
| impact | contract, intake, backbone | cold (unless escalated) |
| frd | contract, backbone, plan | log, cold, warm, other modules |
| stories | contract, backbone | log, cold, warm, other modules |
| srs | contract, backbone, stories | log, cold, other modules |
| wireframes | contract, wireframe_input | log, cold, other modules |
| package | contract | log, cold, warm shards |
| status | contract | log (unless --audit), warm, cold |

## Multi-BA Governance
- Hot shards: Lead BA owns
- Warm module shards: Module BA owns; cross-module = Lead BA approval
- Conflict → escalate before proceeding
- Promotion requires: impact → approval → mutating rerun → file-back with trace schema
- Pre-mutate: verify write authority + approved impact run

## Wireframe-State Behavior
Read-only on upstream BA artifacts. May regenerate only DESIGN.md, wireframe input/map/state.

## Packaging Behavior
Validation-and-compile step, not full rebuild. HTML under `compiled_root`. Markdown = source of truth.

## Token Discipline
Read only the step file needed. Use manifest for group extraction. Reuse summaries over rereading large sources.
