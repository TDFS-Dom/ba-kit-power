---
inclusion: manual
---

# BA-kit Template Catalog

Load khi cần tạo artifact mới. Chứa inline template structures cho fill-in.

## Template Index

| Template | Used For | Step |
|---|---|---|
| Intake Form | Normalize raw input | Step 2 |
| Requirements Backbone | Source of truth after scope lock | Step 5 |
| FRD | Functional requirements document | Step 6 |
| User Story | Agile stories with AC | Step 7 |
| SRS | System specification | Steps 8-11 |
| Wireframe Input | Constraint pack for manual design | Step 8.1 |
| DESIGN.md | Project design system document | Step 8.2 |
| Wireframe Map | Manual handoff checklist | Step 9.4 |
| Project Home | BA-facing dashboard | Steps 4.1, 5 |
| Project Memory | Anti-drift support layer | Step 5 |

## SRS Template Groups (manifest)

| Group | Sections |
|---|---|
| A | Purpose & Scope, Overall Description, Functional Requirements |
| B | Use Case Specifications |
| C | Screen Contract Plus, Screen Inventory |
| D | NFR, Data Flow, ERD, API Specs, Constraints |
| E | Screen Descriptions, Wireframe References, Screen Regions |
| F | Common Rules, Message List, Test Cases, Glossary |

## Writing Rules
- Use Vietnamese by default (unless user requests English)
- Use Mermaid for all diagrams
- Use incremental writes for artifacts >150 lines
- Keep templates as fill-in structures, not overexplained prose
- Maintain traceability IDs across all artifacts

---

## Intake Form Template

```markdown
# Phiếu tiếp nhận yêu cầu (Intake Form)

## Thông tin dự án (Project Information)
| Trường | Giá trị |
|---|---|
| Tên dự án | |
| Ngày | |
| Người yêu cầu | |
| Tài liệu gốc | |

## Bối cảnh kinh doanh (Business Context)
### Vấn đề cần giải quyết
### Mục tiêu kinh doanh
### Các bên liên quan
| Tên / Vai trò | Mức quan tâm / Ảnh hưởng | Ghi chú |
|---|---|---|

## Yêu cầu thô (Raw Requirements)
<!-- Trích nguyên văn từ tài liệu gốc -->

## Màn hình và giao diện
| Màn hình / Thành phần | Mô tả | Ghi chú |
|---|---|---|

## Quy trình và luồng công việc
| Quy trình / Luồng | Mô tả | Ghi chú |
|---|---|---|

## Ràng buộc và giả định
### Ràng buộc
### Giả định

## Tuân thủ và quy định

## Câu hỏi mở

## Ghi chú phân tích
```

---

## Requirements Backbone Template

```markdown
# Xương sống yêu cầu (Requirements Backbone)

**Dự án:** [Tên]  **Slug:** [slug]  **Ngày:** [YYMMDD-HHmm]
**Chế độ:** [lite|hybrid|formal]  **Chủ sở hữu:** [BA]

## Tóm tắt quyết định phạm vi
- Vấn đề kinh doanh:
- Kết quả mong muốn:
- Ngoài phạm vi:
- Quyết định đã chốt:

## Mục tiêu kinh doanh và chỉ số thành công
| Goal ID | Mục tiêu | Chỉ số | Chủ sở hữu |
|---|---|---|---|

## Nhóm người dùng và tác nhân
| Actor ID | Vai trò | Mục tiêu chính | Ghi chú |
|---|---|---|---|

## Ma trận portal
| Portal ID | Portal Name | Target Actor | Owned Screen Families | Default Entry |
|---|---|---|---|---|

## Bản đồ tính năng
| Feature ID | Tính năng | Mô tả | Ưu tiên | In Scope | Ghi chú |
|---|---|---|---|---|---|

## Backbone yêu cầu chức năng
| FR ID | Yêu cầu | Giá trị kinh doanh | Nguồn | AC tóm tắt |
|---|---|---|---|---|

## Backbone yêu cầu phi chức năng
| NFR ID | Danh mục | Yêu cầu | Trigger / Gate |
|---|---|---|---|

## Story Map sơ bộ
| Epic | Capability | Story / Outcome | Ưu tiên | Ghi chú |
|---|---|---|---|---|

## UI và màn hình cần tài liệu
| Screen ID | Portal ID | Màn hình | Phức tạp | Cần wireframe | Ghi chú |
|---|---|---|---|---|---|

## Hướng thiết kế UI cần chốt trước wireframe
- Cần DESIGN.md: [Yes/No]
- Hướng tham chiếu:
- Quyết định cần chốt trước Step 9:

## Gating quyết định artifact
- FRD: [Required/Optional] + lý do
- User stories: [Required/Optional] + lý do
- SRS: [Required/Optional] + lý do
- Wireframes: [Required/Optional] + lý do
- Package HTML: [Required/Optional] + lý do

## Assumptions, Risks, Open Questions
### Assumptions
### Risks
### Open Questions

## Next Step
```

---

## FRD Template

```markdown
# Tài liệu yêu cầu chức năng (FRD)

**Dự án:** [Tên]  **Version:** [v1.0]  **Owner:** [BA]  **Ngày:** [YYYY-MM-DD]

## Tổng quan chức năng
## Chân dung người dùng
| Persona | Mục tiêu | Điểm đau | Tiêu chí thành công |
|---|---|---|---|

## Danh sách tính năng
| Tính năng | Ưu tiên (MoSCoW) | Mô tả | Owner |
|---|---|---|---|

## Luồng nghiệp vụ (Mermaid)
## Yêu cầu dữ liệu
## Quy tắc nghiệp vụ
| Rule ID | Quy tắc | Lý do | Ngoại lệ |
|---|---|---|---|

## Điểm tích hợp
| Hệ thống | Mục đích | Giao diện | Phụ thuộc |
|---|---|---|---|

## Tiêu chí chấp nhận
```

---

## User Story Template

```markdown
# Mẫu User Story

**Epic:** [Epic]  **Feature:** [Feature]  **Story ID:** [US-001]  **Owner:** [BA]

## Story
Với tư cách là [vai trò], tôi muốn [khả năng] để [lợi ích].

## Bối cảnh
- Mục tiêu kinh doanh:
- Nhu cầu người dùng:
- Kịch bản:

## Tiêu chí chấp nhận (Given/When/Then)
- Cho trước [bối cảnh], khi [hành động], thì [kết quả].

## INVEST Check
- Independent / Negotiable / Valuable / Estimable / Small / Testable

## Definition of Ready
- [ ] Vai trò rõ ràng
- [ ] AC đã định nghĩa
- [ ] Phụ thuộc đã xác định
- [ ] Ưu tiên đã xác nhận

## Definition of Done
- [ ] Đáp ứng tất cả AC
- [ ] Stakeholder phê duyệt
- [ ] Tài liệu cập nhật
- [ ] Test cases định nghĩa
```

---

## DESIGN.md Template

```markdown
# DESIGN.md - [Tên dự án]

## Metadata
- Project / Slug / Date / Owner / Reference direction / Status

## 0. Phạm vi áp dụng
## 1. Visual Theme & Atmosphere
## 2. Information Architecture (Portals & Navigation)
### 2.1 Portal Summary
| Portal ID | Portal/App | Target Actor | Owned Screen Families | Notes |
### 2.2 Navigation Schema
| Portal ID | Nav Schema ID | Pattern | Menu Items | Default Landing | Active Rule | Breadcrumb Rule | Exceptions |

## 3. Color Palette & Roles
| Role | Color | Usage | Notes |

## 4. Typography Rules
| Level | Font/Style | Size/Weight | Usage |

## 5. Component Stylings
## 6. Layout Principles
## 7. Depth & Elevation
## 8. Do's and Don'ts
## 9. Responsive Behavior
## 10. Design Handoff Guide
```

---

## Project Home Template

```markdown
# Trang điều phối dự án BA (Project Home)

> Dashboard thân thiện cho BA non-tech. Không thay thế backbone/intake.

**Dự án:** [Tên]  **Slug:** [slug]  **Version:** [YYMMDD-HHmm]
**Chế độ:** [mode]  **Cập nhật:** [date]

## 1. Tôi Đang Ở Đâu?
| Hạng mục | Trạng thái | Ý nghĩa |
|---|---|---|

## 2. Bước Tiếp Theo Được Khuyến Nghị
## 3. Việc Cần User Chốt
| Câu hỏi | Vì sao | Ảnh hưởng |
|---|---|---|

## 4. Bản Đồ Artifact
| Tên BA nhìn thấy | File kỹ thuật | Khi nào dùng |
|---|---|---|

## 5. Prompt Nhanh Theo Runtime
## 6. Từ Điển Tên Gọi Thân Thiện
## 7. Lưu Ý An Toàn
```

---

## Project Memory Template (Compact)

```markdown
# Bộ nhớ dự án (Project Memory) — Compact

**Dự án:** [Tên]  **Slug:** [slug]  **Ngày:** [YYMMDD-HHmm]
**Mode:** compact  **Activation Level:** [Base|Modular|Program]
**Last Refresh Source:** [intake|backbone|impact]

## Canonical Vocabulary
| Memory ID | Loại | Thuật ngữ chuẩn | Diễn giải | Nguồn | Trạng thái |
|---|---|---|---|---|---|

## Approved Decisions
| Decision ID | Chủ đề | Quyết định | Nguồn xác nhận | Ảnh hưởng artifact |
|---|---|---|---|---|

## Accepted Assumptions
| Assumption ID | Giả định | Điều kiện hiệu lực | Nguồn | Rà lại khi |
|---|---|---|---|---|

## Rejected Assumptions
| Reject ID | Không được suy diễn lại | Lý do | Nguồn | Ghi chú |
|---|---|---|---|---|

## Accepted Corrections
| Correction ID | Phát biểu thay đổi | Node bị ảnh hưởng | Cách xử lý | Ngày |
|---|---|---|---|---|

## Push-back Triggers
| Trigger ID | Dấu hiệu dừng | Câu hỏi / hành động bắt buộc |
|---|---|---|
```

---

## Wireframe Input Pack Template (Structure)

Sections required:
1. Artifact Set Information (slug, date, module, app type, source paths)
2. Manual Wireframe Preparation Rules
3. Approved Design Decisions Snapshot
4. Use Case Excerpts (per screen)
5. Screen Contract Plus table
6. Screen Inventory table
7. Proposed Artifact Groups
8. Portal Snapshot
9. Menu Matching Checklist
10. Active Menu Evidence Requirement
11. Navigation Exceptions
12. Non-Negotiable Constraints
13. Final Document Attachment Guide
14. Stop Conditions

---

## Wireframe Map Template (Structure)

Sections required:
1. Artifact Set Information
2. Artifact Summary (scope, portals, screens per artifact)
3. Screen To Final Document Mapping
4. Supporting Screen Inventory
5. Navigation Exceptions
6. User Action Checklist
7. Coverage Checks
