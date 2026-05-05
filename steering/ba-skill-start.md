---
inclusion: manual
---

# BA-kit Skill — ba-start (Lifecycle Engine)

Lifecycle engine cho BA-kit. Accepts raw requirements, normalizes, locks scope, builds backbone, emits downstream artifacts, packages deliverables.

## Invocation
```
ba-start
ba-start intake <file>
ba-start impact --slug <slug> [change-file]
ba-start backbone --slug <slug>
ba-start frd --slug <slug> --module <module_slug>
ba-start stories --slug <slug> --module <module_slug>
ba-start srs --slug <slug> --module <module_slug>
ba-start wireframes --slug <slug> --module <module_slug>
ba-start package --slug <slug>
ba-start status --slug <slug>
ba-start next --slug <slug>
```

## Step Dispatch

| Command | Load steering | Notes |
|---|---|---|
| no subcommand | `ba-steps-intake.md` then downstream | full lifecycle |
| intake | `ba-steps-intake.md` | Steps 1-4 |
| impact | `ba-impact.md` | analysis only |
| backbone | `ba-steps-backbone.md` | Step 5 |
| frd | `ba-steps-frd.md` | Step 6 |
| stories | `ba-steps-stories.md` | Step 7 |
| srs | `ba-steps-srs-core.md` | SRS router; loads narrower SRS steps on demand |
| wireframes | `ba-steps-wireframes.md` | Step 9 standalone |
| package | `ba-steps-package.md` | Step 12 |
| status | `ba-steps-status.md` | inspection only |
| next | `ba-skill-next.md` | recommendation; no mutation |

## Fast Execution Contract
1. Parse arguments before doing any work
2. Resolve command and target scope with exact matching only
3. Enforce prerequisites from contract data
4. Stop on ambiguity instead of guessing
5. Ask before overwriting any mutable target
6. Keep accepted rerun step locked once user approves

## Stop Conditions
- Never silently choose slug/date/module by mtime
- Never use broad `*-{slug}*` matching
- Never mutate artifacts from bare change statement → route through `impact`
- Never delegate merge or packaging assembly of large artifacts
