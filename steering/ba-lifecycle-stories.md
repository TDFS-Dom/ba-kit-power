---
inclusion: manual
---

# BA Lifecycle — User Stories

> **⚠️ DEPRECATED:** Prefer `ba-steps-stories.md` which contains the full step logic. This file is kept for backward compatibility only.

Load file này khi produce user stories (Step 7).

## Prerequisites
- `paths.backbone` must exist
- Module must be resolved
- If backbone missing → print path + stop

## Step 7 — Produce User Stories

Template per story:

```markdown
# User Stories — [Module Name]

## Epic: [Epic Name]

### US-001: [Story Title]

**Story:** Với tư cách là [vai trò], tôi muốn [khả năng] để [lợi ích].

**Acceptance Criteria:**
- Cho trước [bối cảnh], khi [hành động], thì [kết quả].
- Cho trước [bối cảnh], khi [hành động], thì [kết quả].

**INVEST Check:**
- Independent: [Yes/No + note]
- Negotiable: [Yes/No]
- Valuable: [Yes/No]
- Estimable: [Yes/No]
- Small: [Yes/No]
- Testable: [Yes/No]

**Priority:** [Must/Should/Could]
**Linked Screens:** [SCR-xx]
**Linked Features:** [F-xx]
```

Save to `plans/{slug}-{date}/03_modules/{module_slug}/user-stories.md`

## Execution Rules
- Start from backbone feature map and FR draft
- Pull FRD only when it already exists
- Generate Given/When/Then acceptance criteria
- Validate INVEST for each story
- Include story-to-screen alignment when UI exists
- Group by Epic → Feature → Story
