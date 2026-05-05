---
inclusion: always
---

# BA Quality Standards

Rules áp dụng cho MỌI BA artifact. Load cùng với ba-contract.md.

## Requirements Quality
- Every requirement has clear source, business rationale, and owner
- Every requirement has acceptance criteria or validation guidance
- Every requirement is unambiguous, testable, and prioritized
- One intent per statement — no bundled behaviors
- SMART: specific, measurable, achievable, relevant, time-bound

## Stories Quality
- Follow `As a / I want / so that` structure
- Acceptance criteria specific enough to verify without interpretation
- Boundary conditions and failure cases captured
- INVEST validated

## Traceability
- Business goals → requirements → downstream artifacts
- Cross-references explicit and easy to follow
- FRD features → user stories → SRS requirements (full chain)

## Cross-Artifact Consistency (CRITICAL)

| Check | Rule |
|---|---|
| UC ↔ Screen | UC actor actions = screen User Actions (same wording, same sequence) |
| UC ↔ Screen | UC system responses = screen Behaviour Rules |
| UC ↔ Screen | UC alternate flows reflected in screen Error/States |
| Stories ↔ SRS | Story AC covered by UC postconditions + screen Validation Rules |
| FRD ↔ Stories ↔ SRS | FRD features fully traceable through stories into SRS |
| Fields | Field names identical across UC steps, screen tables, wireframe labels |
| Navigation | Portal ID, Nav Schema ID, Expected Active Menu Item consistent everywhere |
| Screen descriptions | Must NOT redefine portal/nav/active behavior locked upstream |

## Screen Description Rules

### Field Table Separation
- **Display Rules**: visibility, defaults, read-only, formatting
- **Behaviour Rules**: on-change actions, navigation triggers, dependent fields
- **Validation Rules**: required, format, range, cross-field, error messages

### Centralization
- Reusable cross-screen rules → Common Rules section, reference by `CR-{TYPE}-{NN}`
- Reusable messages → Message List section, reference by `MSG-{TYPE}-{NN}`
- TYPE for rules: DIS, BEH, VAL, MIX
- TYPE for messages: ERR, WRN, SUC, INF
- NN = 2-digit unique sequence within SRS

### Navigation Consistency
- Same portal → same Nav Schema ID (unless exception declared)
- Global nav visible → must show correct active/selected state
- Hidden nav → document exception explicitly
- Modal/drawer/dialog with own flow logic = primary screen (own SCR-xx ID)

## Anti-Patterns (NEVER do)
- ❌ Copy-paste rules between screens (centralize + reference)
- ❌ Redefine portal/nav behavior in final screen descriptions
- ❌ Mix local ad-hoc code formats with standard CR-/MSG- format
- ❌ Leave orphaned requirements without business justification
- ❌ Bundle multiple behaviors in one requirement statement
- ❌ Guess missing upstream context (stop and ask instead)

## Fail-Closed Behavior
- If required fact missing → mark as assumption or open question
- If downstream artifact requires guessing upstream decision → stop and route back
- If correction invalidates persisted assumption → record rejection in project memory
- Material uncertainty → stop and ask instead of filling with plausible prose
