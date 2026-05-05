---
inclusion: manual
---

# BA-kit Skill — ba-do (Freeform Router)

Route freeform BA text to the right BA-kit command automatically. This is a dispatcher — does NOT do downstream work itself.

## Invocation
```
ba-do xem next step cho project nay
ba-do dang lam do SRS thi them yeu cau nay
ba-do toi nhan module auth-flow
ba-do gui module payment cho Lead BA review
ba-do publish SRS len Notion
```

## Routing Table

| If text describes... | Route to | Why |
|---|---|---|
| publishing to Notion | `ba-notion` | publish workflow |
| claiming/assigning module, review, conflict check, PR/commit/merge | `ba-collab` | collaboration |
| checking status/completion/missing artifacts | `status` | inspection |
| continue project / resume / "toi nen lam gi tiep" | `ba-next` | continuation |
| what next step should be | `ba-next` | state-aware recommendation |
| adding/changing/removing requirement/rule/scope | `ba-impact` | change triage |
| bare correction statement in existing project | `ba-impact` | safe default |
| prepare UI handoff / mockup checklist / wireframe constraints | `wireframes` | friendly alias |
| export / publish review package / stakeholder HTML | `package` | friendly alias |
| directly naming intake/backbone/frd/stories/srs/wireframes/package | `ba-start` with matching subcommand | direct lifecycle |
| new BA engagement from raw input | `ba-start` | full lifecycle |

## Priority Rule
If text could match both `ba-impact` and direct edit → prefer `ba-impact` unless user explicitly says update/edit/overwrite/regenerate/rerun.

## Display Format
```
BA-kit Routing
Input: {short excerpt}
Routing to: {command}
Reason: {one-line reason}
```
Then dispatch to chosen command and stop. Dispatcher must NOT mutate artifacts.
