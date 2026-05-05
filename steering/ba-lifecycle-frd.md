---
inclusion: manual
---

# BA Lifecycle — FRD

> **⚠️ DEPRECATED:** Prefer `ba-steps-frd.md` which contains the full step logic. This file is kept for backward compatibility only.

Load file này khi produce Functional Requirements Document (Step 6).

## Prerequisites
- `paths.backbone` must exist
- Module must be resolved
- If backbone missing → print path + stop

## Step 6 — Produce FRD

Template structure:

```markdown
# Tài liệu yêu cầu chức năng (FRD)

**Dự án:** [Tên]
**Phiên bản:** v1.0
**Chủ sở hữu:** [BA]
**Ngày:** [YYYY-MM-DD]

## Tổng quan chức năng (Functional Overview)

## Chân dung người dùng (User Personas)
| Persona | Mục tiêu | Điểm đau | Tiêu chí thành công |

## Danh sách tính năng (Feature List)
| Tính năng | Ưu tiên (MoSCoW) | Mô tả | Chủ sở hữu |

## Luồng nghiệp vụ (Workflows)
(Mermaid flowcharts/swimlanes)

## Yêu cầu dữ liệu (Data Requirements)
- Đầu vào / Đầu ra / Validation / Storage

## Quy tắc nghiệp vụ (Business Rules)
| Rule ID | Quy tắc | Lý do | Ngoại lệ |
| BR-01 | | | |

## Điểm tích hợp (Integration Points)
| Hệ thống | Mục đích | Giao diện | Phụ thuộc |

## Tiêu chí chấp nhận (Acceptance Criteria)
```

Save to `plans/{slug}-{date}/03_modules/{module_slug}/frd.md`

## Execution Rules
- Start from backbone only (+ plan when exists)
- In `hybrid` mode: concise, focused on features/workflows/business rules/integrations
- In `lite` mode: emit only when user explicitly asks
- Use Mermaid for all diagrams
