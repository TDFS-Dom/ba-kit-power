---
inclusion: manual
---

# BA Lifecycle — Intake

> **⚠️ DEPRECATED:** Prefer `ba-steps-intake.md` which contains the full step logic from the source repo. This file is kept for backward compatibility only.

Load file này khi tạo dự án BA mới (Steps 1-4).

## Prerequisites
- Raw input: file path (PDF, MD, TXT, DOCX) hoặc pasted text
- Nếu không có input → prompt user

## Step 1 — Accept Input

Chấp nhận:
- File path → read content
- Pasted text → use directly
- Images → multimodal reading

## Step 2 — Parse and Normalize

Extract vào Intake Form template:

```markdown
# Phiếu tiếp nhận yêu cầu (Intake Form)

## Thông tin dự án
| Trường | Giá trị |
|---|---|
| Tên dự án | |
| Ngày | |
| Người yêu cầu | |
| Tài liệu gốc | |

## Bối cảnh kinh doanh
### Vấn đề cần giải quyết
### Mục tiêu kinh doanh
### Các bên liên quan
| Tên / Vai trò | Mức quan tâm / Ảnh hưởng | Ghi chú |

## Yêu cầu thô
(Trích nguyên văn từ tài liệu gốc)

## Màn hình và giao diện
| Màn hình / Thành phần | Mô tả | Ghi chú |

## Quy trình và luồng công việc
| Quy trình / Luồng | Mô tả | Ghi chú |

## Ràng buộc và giả định
### Ràng buộc
### Giả định

## Tuân thủ và quy định

## Câu hỏi mở

## Ghi chú phân tích
```

Save to `plans/{slug}-{date}/01_intake/intake.md`

## Step 3 — Gap Analysis

Review intake against BA completeness checklist:
- Stakeholders identified with roles?
- Clear problem statement + measurable goal?
- Scope boundaries defined (in/out)?
- Success criteria / KPIs stated?
- Compliance / regulatory mentioned?
- UI screens described enough for wireframe?
- Processes described enough to map?

Flag each gap explicitly.

## Step 4 — Clarifying Questions + Scope Lock

Present 3-8 targeted questions covering:
- Output language preference
- Missing stakeholders
- Ambiguous scope boundaries
- Unstated success criteria
- Regulatory context
- Priority / sequencing
- Engagement mode (default: hybrid)

Incorporate answers back into intake form.

## Step 4.1 — Generate Work Plan

Produce scoped work plan → save to `plans/{slug}-{date}/01_intake/plan.md`

Create PROJECT-HOME.md (BA-facing dashboard):
- Current lifecycle state
- Recommended next step
- Decisions user must make
- Quick prompts for resume

Mode defaults:
- `lite`: intake + backbone + stories
- `hybrid`: intake + backbone + stories + targeted FRD/SRS
- `formal`: full artifact suite
