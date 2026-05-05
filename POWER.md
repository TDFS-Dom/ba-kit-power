---
name: "ba-kit-power"
displayName: "BA-kit Power"
description: "Build full-stack BA deliverables with structured lifecycle, templates, and quality gates — intake → backbone → FRD → stories → SRS → wireframe handoff → package"
keywords: ["business analysis", "BA", "requirements", "SRS", "FRD", "user stories", "use cases", "wireframe", "intake", "backbone", "stakeholder", "handoff", "specification"]
author: "TDFS-Dom"
---

# BA-kit Power

BA-kit biến Kiro thành một BA workstation có lifecycle rõ ràng, artifact có cấu trúc, và handoff chuẩn cho stakeholder/engineering.

## Capabilities

- **Full BA lifecycle**: intake → backbone → FRD → stories → SRS → wireframe handoff → package
- **Change impact triage**: phân tích ảnh hưởng trước khi sửa artifact
- **NLP routing**: BA non-tech dùng ngôn ngữ tự nhiên, agent tự route đúng workflow
- **Multi-module governance**: phân chia module, review, conflict detection
- **Template-backed artifacts**: mọi deliverable đều có template chuẩn
- **Incremental writes**: tránh token truncation cho artifact lớn
- **Quality gates**: cross-artifact consistency, traceability, SMART validation

## Quick Start

### Bắt đầu dự án mới
```
Tôi có tài liệu yêu cầu mới, hãy tạo dự án BA
```

### Tiếp tục dự án
```
Tiếp tục dự án warehouse-rfp, bước tiếp theo là gì?
```

### Đánh giá thay đổi
```
Đánh giá thay đổi: Export CSV phải có audit log
```

### Chuẩn bị wireframe handoff
```
Chuẩn bị handoff UI cho module auth-flow
```

### Xuất gói bàn giao
```
Xuất gói bàn giao cho stakeholder
```

## Steering Files

### Always-loaded (inclusion: always)
| File | Mục đích |
|---|---|
| `ba-contract.md` | Contract summary: paths, resolution, behavior rules |
| `ba-routing.md` | NLP intent → command routing dispatcher |

### Core Contract (inclusion: manual — load khi cần full contract)
| File | Mục đích |
|---|---|
| `ba-contract-data.md` | Full contract YAML: paths, prerequisites, states, activation thresholds |
| `ba-contract-behavior.md` | Full behavior policy: routing, recovery, execution lock, governance |

### Lifecycle Steps (inclusion: manual — load per active command)
| File | Mục đích |
|---|---|
| `ba-steps-intake.md` | Steps 1-4: accept input, parse, gap analysis, scope lock |
| `ba-steps-backbone.md` | Step 5: requirements backbone (source of truth) |
| `ba-steps-frd.md` | Step 6: FRD production |
| `ba-steps-stories.md` | Step 7: user stories |
| `ba-steps-srs-core.md` | Steps 8-11 router + Groups A/B/C + wireframe constraint pack |
| `ba-steps-srs-wireframes.md` | Steps 8.2, 9, 10: design decisions + final screen descriptions |
| `ba-steps-srs-assembly.md` | Steps 10.1, 11: validation pack + assembly |
| `ba-steps-wireframes.md` | Step 9 standalone: manual wireframe handoff |
| `ba-steps-package.md` | Step 12: HTML packaging + delivery |
| `ba-steps-status.md` | Status inspection |

### Skills (inclusion: manual — load per workflow)
| File | Mục đích |
|---|---|
| `ba-skill-start.md` | Lifecycle engine: dispatch table + execution contract |
| `ba-skill-do.md` | Freeform router: NLP → command dispatch |
| `ba-skill-next.md` | Next step detection: state-aware recommendation |
| `ba-skill-collab.md` | Collaboration: module ownership, review, GitHub handoff |
| `ba-skill-notion.md` | Notion publishing: push artifacts to Notion via MCP |

### Domain Rules & Templates (inclusion: manual)
| File | Mục đích |
|---|---|
| `ba-impact.md` | Change impact triage workflow |
| `ba-quality-rules.md` | Quality standards + consistency checks |
| `ba-templates.md` | Full template catalog with inline structures |
| `ba-delegation.md` | Multi-BA governance + collaboration rules |

### Support (inclusion: manual)
| File | Mục đích |
|---|---|
| `ba-agents.md` | Agent delegation specs (4 specialists) |
| `ba-token-budget.md` | Token budget guardrails + load strategy |

### Deprecated (kept for backward compat — prefer `ba-steps-*` equivalents)
| File | Replaced by |
|---|---|
| `ba-lifecycle-intake.md` | `ba-steps-intake.md` |
| `ba-lifecycle-backbone.md` | `ba-steps-backbone.md` |
| `ba-lifecycle-frd.md` | `ba-steps-frd.md` |
| `ba-lifecycle-stories.md` | `ba-steps-stories.md` |
| `ba-lifecycle-srs.md` | `ba-steps-srs-core.md` + `ba-steps-srs-wireframes.md` + `ba-steps-srs-assembly.md` |
| `ba-lifecycle-wireframes.md` | `ba-steps-wireframes.md` |
| `ba-lifecycle-package.md` | `ba-steps-package.md` |

## Workflow Overview

```
Raw input → Intake + Gap Analysis → PROJECT-HOME.md
→ Requirements Backbone (scope lock)
→ Module artifacts: FRD / Stories / SRS / Screen Contract Plus
→ DESIGN.md + wireframe-input.md + wireframe-map.md
→ User tự tạo mockup / wireframe
→ Final SRS + HTML package
```

## Directory Structure (Output)

```
plans/
  {slug}-{date}/
    PROJECT-HOME.md
    01_intake/
      intake.md
      plan.md
    02_backbone/
      backbone.md
      project-memory.md
    03_modules/
      {module_slug}/
        frd.md
        user-stories.md
        srs.md
        wireframe-input.md
        wireframe-map.md
    04_compiled/
      compiled-frd.html
      compiled-srs.html

designs/
  {slug}/
    DESIGN.md
```

## Defaults

- Language: Vietnamese (unless user requests English)
- Mode: `hybrid` (backbone + targeted FRD + stories + selective SRS)
- UI baseline: Shadcn UI (overridden by project DESIGN.md)
- Date format: `YYMMDD-HHmm`

