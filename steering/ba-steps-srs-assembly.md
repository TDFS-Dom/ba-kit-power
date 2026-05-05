---
inclusion: manual
---

# BA Step — SRS Assembly (Steps 10.1, 11)

Load sau khi Groups A-E hoàn tất.

## Step 10.1 — Validation pack (Group F)
- Test Cases
- Glossary
- Traceability cross-references

## Step 11 — Assembly + quality review

Assembly procedure (INLINE, never delegate):
1. Write SRS skeleton to `paths.srs` using template heading structure
2. For each group (A→B→C→D→E→F): read fragment → edit-append into skeleton
3. Cross-artifact consistency check:
   - UC steps ↔ screen fields/actions
   - Screen Contract Plus ↔ wireframe constraints ↔ final descriptions
   - UC actor actions = screen User Actions (same wording)
   - UC system responses = screen Behaviour Rules
   - Alternate flows reflected in screen error states
   - Story AC covered by UC postconditions + screen validation
   - Final screen descriptions do NOT redefine Portal ID/Nav Schema ID/active behavior
4. Resolve placeholder references
5. Verify every SCR and UC traces to user stories
6. Delete group fragments after verified merge

Execution order:
```
Group A → Group B → Group D
Group B → Group C
Group C → Wireframes
Wireframes → Group E
Group E → Group F
Group F → Assembly
```
