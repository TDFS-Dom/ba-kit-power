---
inclusion: manual
---

# BA-kit Skill — ba-next (Next Step Detection)

Detect the next logical BA step from current artifact set. Read-only — no mutation.

## Process

1. **Resolve project**: slug + dated set using contract. If ambiguous → stop and ask.

2. **Inspect artifacts**: Check which exist:
   - intake, backbone, frd, stories, srs, wireframe-input, wireframe-map, wireframe-state, packaged HTML
   - Read backbone gate section when exists

3. **Determine next step** (first matching rule):
   1. No intake → `ba-start intake`
   2. Intake exists, no backbone → `ba-start backbone --slug <slug>`
   3. Backbone exists, FRD required but missing → `ba-start frd --slug <slug>`
   4. Backbone exists, stories missing → `ba-start stories --slug <slug>`
   5. SRS required and missing → `ba-start srs --slug <slug>`
   6. wireframe-input exists, wireframe-state missing, handoff required → `ba-start wireframes --slug <slug>`
   7. Final markdown exists, packaged HTML missing → `ba-start package --slug <slug>`
   8. Everything required exists → `ba-start status --slug <slug>`

   When gates unclear → recommend `status` instead of guessing.

4. **Display**:
```
BA Next
Project: {slug}
Date set: {date}
Project Home: {exists/missing}
Next command: /ba-start ...
BA-facing next step: ...
Reason: ...
```

Do NOT mutate artifacts.
