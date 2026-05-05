---
inclusion: always
---

# BA-kit Routing

Khi user dùng ngôn ngữ tự nhiên, route intent theo bảng sau. Đây là dispatcher — KHÔNG tự làm downstream work.

## Routing Table

| User nói... | Route to | Lý do |
|---|---|---|
| Tạo dự án mới / phân tích tài liệu mới | `intake` (full lifecycle) | New engagement |
| Tiếp tục dự án / bước tiếp theo | Inspect artifacts → recommend next step | State-aware continuation |
| Đánh giá thay đổi / thêm yêu cầu / sửa requirement | `impact` | Change triage before mutation |
| Bare correction statement (e.g., "Không có nhóm admin user") | `impact` | Safe default |
| Chuẩn bị handoff UI / wireframe constraints | `wireframes` | Manual wireframe handoff |
| Xuất gói bàn giao / export HTML | `package` | Packaging |
| Kiểm tra trạng thái | `status` | Inspection |
| Nhận module / gửi review / tạo PR | Collaboration workflow | Module teamwork |
| Directly naming a step (backbone, frd, stories, srs) | That specific step | Explicit lifecycle |

## Routing Priority

Khi ambiguous giữa `impact` và direct edit:
- **Prefer `impact`** unless user explicitly says "update", "overwrite", "regenerate", or "rerun" a named artifact

## Natural Language Aliases

| BA nói | Agent hiểu |
|---|---|
| Tạo dự án mới | intake |
| Tiếp tục dự án | next → recommended step |
| Khung yêu cầu | backbone |
| Đánh giá thay đổi | impact |
| Chuẩn bị handoff UI | wireframes |
| Xuất gói bàn giao | package |
| Kiểm tra trạng thái | status |

## Display Format

After routing, show:
```
BA-kit Routing
Input: {short excerpt}
Routing to: {command}
Reason: {one-line reason}
```

Then execute the routed command.
