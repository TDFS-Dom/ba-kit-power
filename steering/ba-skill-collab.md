---
inclusion: manual
---

# BA-kit Skill — ba-collab (Collaboration & GitHub Handoff)

Route BA-friendly collaboration requests into module ownership, review packets, and optional approval-gated GitHub handoff.

## Invocation
```
ba-collab Tôi nhận module auth-flow
ba-collab Kiểm tra module payment trước khi gửi review
ba-collab Tôi làm xong module payment, gửi Lead BA review
ba-collab Lead BA approve module auth-flow
ba-collab Tạo PR cho module auth-flow
```

## Intent Classification

| BA says | Internal action |
|---|---|
| create collaboration workspace / chia module | initialize COLLAB-HOME + module homes |
| tôi nhận module X / assign module X cho Y | claim or assign module |
| kiểm tra module X trước review | pre-review check |
| làm xong module X / gửi Lead BA review | create review packet; optional PR after approval |
| cập nhật theo feedback | mark changes-requested or in-progress |
| approve module X | mark approved (Lead BA only) |
| tổng hợp module đã approve | mark integrated after confirmation |
| tạo PR / push / merge | external GitHub handoff; require explicit approval |

## Module Status Values
unassigned → assigned → in-progress → ready-for-review → changes-requested → approved → integrated → blocked

## Review Status Values
none → local-packet → draft-pr → review-requested → changes-requested → approved → merged → conflict

## Rules
- Never mutate lifecycle artifacts from collab intent. If changes requirements → route `impact` first
- Verify module owner before marking ready-for-review or approved
- Flag cross-module escalation (backbone, DESIGN.md, hot/global memory changes)
- GitHub actions (commit, push, PR, merge) = external side effects → require explicit approval with action plan shown first

## Display
```
BA Collaboration
Project: {slug}
Module: {module}
Action: {friendly action}
Status: {module status}
Review: {review status}
Updated: {paths}
Next: {next step}
External GitHub action: {not requested | approval required | completed}
```
