---
inclusion: manual
---

# BA-kit — Delegation & Collaboration

Load file này khi teamwork, module split, hoặc multi-BA governance cần thiết.

## Module Collaboration Workflow

### BA-Friendly Actions

| BA nói | Action |
|---|---|
| Tôi nhận module X | Claim module ownership |
| Kiểm tra module X trước review | Pre-review check |
| Gửi module X cho Lead BA review | Create review packet |
| Approve module X | Mark approved (Lead BA only) |
| Tổng hợp module đã approve | Mark integrated |

### Module Status Values
`unassigned → assigned → in-progress → ready-for-review → changes-requested → approved → integrated → blocked`

### Review Status Values
`none → local-packet → draft-pr → review-requested → changes-requested → approved → merged → conflict`

## Delegation Rules

### Narrow Handoff Packets
Each delegated packet contains ONLY:
- Objective
- Target artifact path
- Allowed write scope
- Exact upstream excerpts (not full documents)
- Trace IDs
- Expected output sections

### Never Delegate
- Assembly/merge of large artifacts (SRS groups, FRD sections)
- HTML conversion of large artifacts
- Sub-agents have limited output tokens — merged SRS exceeds budget

### Repartition Protocol
If delegated scope too large:
- Worker returns `NEEDS_REPARTITION`
- Identifies overloaded section + reason
- Proposes smallest viable split
- Lists exact upstream inputs needed

## Multi-BA Governance

### Memory Ownership

| Layer | Owner | Who May Write |
|---|---|---|
| project-memory.md (compact) | Lead BA | Lead BA |
| hot/ shards | Lead BA | Lead BA |
| warm/modules/{module}.md | Module BA | Module BA (cross-module → escalate) |

### Conflict Rules
- Module BA writing global hot shard → escalate to Lead BA
- Two BAs claiming same shard → escalate
- Warm shard change creating cross-module dependency → Lead BA approval
- Ambiguous ownership → escalate (never guess)

### Safe Mutation Protocol
1. Only owning BA initiates mutating rerun for their scope
2. All memory promotions require explicit approval + trace metadata
3. Cross-module changes require Lead BA sign-off
4. Module artifacts introducing cross-module dependencies → flag + escalate

### Code Uniqueness
- `CR-{TYPE}-{NN}` codes must be unique across ALL modules
- `MSG-{TYPE}-{NN}` codes must be unique across ALL modules
- If redefining shared rule → escalate to backbone layer

## Collaboration Artifacts

### COLLAB-HOME.md
Dashboard for team collaboration:
- Module assignment table
- Review status per module
- Blockers and escalations
- Integration status

### MODULE-HOME.md
Per-module dashboard:
- Module scope (from backbone)
- Owner
- Artifact checklist
- Review status
- Blockers

### Review Packet
Created when module BA sends for review:
- Module scope summary
- Changed artifacts list
- Key decisions made
- Open questions for Lead BA
- Cross-module impact assessment

## External Side Effects (Git/GitHub)

Commit, push, PR, merge are EXTERNAL side effects. Before any:
1. Print exact action plan
2. Print files to be included
3. Print proposed branch/commit/PR title
4. Ask for explicit approval
5. If no approval → stop after local review packet
