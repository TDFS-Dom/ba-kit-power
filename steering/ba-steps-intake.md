---
inclusion: manual
---

# BA Step — Intake (Steps 1-4)

Load khi chạy `ba-start intake`.

## Memory Read Scope
- Must read: contract
- May read: `project_memory` (compact only)
- Must NOT read: memory shards, log, cold

## Prerequisites
- Raw input as file path or pasted text
- `--slug` may override derived project slug

## Step 1 — Accept input
Ask user for: file path (PDF, MD, TXT, image, DOCX) or pasted text.
- PDF: prefer source-extract first, then read cached summary + relevant chunks
- MD/TXT: read directly
- Images: multimodal reading
- DOCX: multimodal or ask export to PDF/MD
- If staged source cache exists under `_source-cache/{hash}` → reuse

## Step 2 — Parse and normalize
Extract into intake form template:
- Project name, date, requester
- Business context (problem, goals, stakeholders)
- Raw requirements (verbatim)
- Screens/UI mentioned
- Processes/workflows mentioned
- Constraints, assumptions, compliance
- Open questions

Save to `paths.intake`.

## Step 3 — Gap analysis
Review against BA completeness checklist:
- Stakeholders identified with roles?
- Clear problem statement + measurable goal?
- Scope boundaries (in/out)?
- Success criteria/KPIs?
- Compliance/regulatory?
- UI screens described enough for wireframe constraints?
- Processes described enough to map?

Flag each gap explicitly.

## Step 4 — Clarifying questions + scope lock
Present 3-8 targeted questions on: language, missing stakeholders, ambiguous scope, unstated success criteria, regulatory context, priority, engagement mode.

Incorporate answers back into intake.

## Step 4.1 — Generate work plan
Produce scoped work plan → save to `paths.plan`.
Create/refresh `paths.project_home` (BA-facing dashboard).

Mode defaults:
- `lite`: intake + backbone + stories
- `hybrid`: intake + backbone + stories + targeted FRD/SRS
- `formal`: full artifact suite
