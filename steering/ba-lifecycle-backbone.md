---
inclusion: manual
---

# BA Lifecycle — Backbone

> **⚠️ DEPRECATED:** Prefer `ba-steps-backbone.md` which contains the full step logic. This file is kept for backward compatibility only.

Load file này khi build requirements backbone (Step 5).

## Prerequisites
- `plans/{slug}-{date}/01_intake/intake.md` must exist
- If missing → print path + stop

## Step 5 — Build Requirements Backbone

Create source-of-truth artifact. Template structure:

```markdown
# Xương sống yêu cầu (Requirements Backbone)

**Dự án:** [Tên]
**Slug:** [slug]
**Ngày:** [YYMMDD-HHmm]
**Chế độ:** [lite | hybrid | formal]

## Tóm tắt quyết định phạm vi (Scope Lock Summary)
- Vấn đề kinh doanh:
- Kết quả mong muốn:
- Ngoài phạm vi:
- Quyết định đã chốt:

## Mục tiêu kinh doanh và chỉ số thành công
| Goal ID | Mục tiêu | Chỉ số | Chủ sở hữu |
| BG-01 | | | |

## Nhóm người dùng và tác nhân
| Actor ID | Vai trò | Mục tiêu chính | Ghi chú |
| ACT-01 | | | |

## Ma trận portal (Portal Matrix)
| Portal ID | Portal Name | Target Actor | Owned Screen Families | Default Entry |
| PORTAL-01 | | | | |

## Bản đồ tính năng (Feature Map)
| Feature ID | Tính năng | Mô tả | Ưu tiên | In Scope | Ghi chú |
| F-01 | | | Must/Should/Could | Yes/No | |

## Backbone yêu cầu chức năng
| FR ID | Yêu cầu | Giá trị kinh doanh | Nguồn | AC tóm tắt |
| FR-01 | | | | |

## Backbone yêu cầu phi chức năng
| NFR ID | Danh mục | Yêu cầu | Trigger / Gate |
| NFR-01 | | | |

## Story Map sơ bộ
| Epic | Capability | Story / Outcome | Ưu tiên |

## UI và màn hình cần tài liệu
| Screen ID | Portal ID | Màn hình | Phức tạp | Cần wireframe |
| SCR-01 | | | Low/Med/High | Yes/No/Critical-only |

## Artifact Emission Gates
- FRD: [Required/Optional] + lý do
- User stories: [Required/Optional] + lý do
- SRS: [Required/Optional] + lý do
- Wireframes: [Required/Optional] + lý do
- Package HTML: [Required/Optional] + lý do

## Assumptions, Risks, Open Questions
```

Save to `plans/{slug}-{date}/02_backbone/backbone.md`

## After Backbone

Initialize project memory:
```markdown
# Bộ nhớ dự án (Project Memory)

## Canonical Vocabulary
| Term | Definition | Source |

## Approved Decisions
| Decision | Rationale | Date |

## Accepted Assumptions
| Assumption | Trigger for re-validation |

## Rejected Assumptions / False Trails
| Rejected | Reason |

## Push-back Triggers
| Trigger | Action |
```

Save to `plans/{slug}-{date}/02_backbone/project-memory.md`

Refresh PROJECT-HOME.md with scope lock summary, artifact gates, next step.

## Rules
- Backbone is primary authoring source after intake
- Do not draft FRD/stories/SRS directly from raw intake once backbone exists
- When UI-backed scope exists, lock portal ownership here before module screen work
- Keep concise and decision-oriented
