# BA-kit Power for Kiro

> Biến Kiro IDE thành một BA workstation có lifecycle rõ ràng, artifact có cấu trúc, và handoff chuẩn cho stakeholder/engineering.

## Tính năng chính

- **Full BA lifecycle**: intake → backbone → FRD → stories → SRS → wireframe handoff → package
- **Change impact triage**: phân tích ảnh hưởng trước khi sửa artifact
- **NLP routing**: dùng ngôn ngữ tự nhiên, agent tự route đúng workflow
- **Multi-module governance**: phân chia module, review, conflict detection
- **Template-backed artifacts**: mọi deliverable đều có template chuẩn
- **Quality gates**: cross-artifact consistency, traceability, SMART validation

## Cài đặt vào Kiro

### Cách 1: Từ GitHub URL (khuyến nghị)

1. Mở Kiro IDE
2. Mở Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
3. Tìm **"Kiro: Install Power"** hoặc **"Kiro: Configure Powers"**
4. Chọn **"Install from GitHub"**
5. Nhập URL repo:
   ```
   https://github.com/phamquangviet891/ba-kit-power
   ```
6. Kiro sẽ tự động nhận diện `POWER.md` + thư mục `steering/` và cài đặt

### Cách 2: Clone thủ công

1. Clone repo vào thư mục powers của Kiro:
   ```bash
   git clone https://github.com/phamquangviet891/ba-kit-power.git ~/.kiro/powers/ba-kit-power
   ```

2. Hoặc clone vào workspace rồi link:
   ```bash
   git clone https://github.com/phamquangviet891/ba-kit-power.git
   ```

3. Restart Kiro — power sẽ xuất hiện trong danh sách Powers

### Cách 3: Copy trực tiếp

1. Download/clone repo này
2. Copy toàn bộ thư mục `ba-kit-power/` (chứa `POWER.md` + `steering/`) vào vị trí powers của Kiro
3. Restart Kiro

## Cấu trúc Power

```
ba-kit-power/
├── POWER.md                          # Power manifest + documentation
├── README.md                         # File này
└── steering/                         # 32 steering files
    ├── ba-contract.md                # [always] Contract summary
    ├── ba-routing.md                 # [always] NLP routing
    ├── ba-contract-data.md           # Full contract YAML
    ├── ba-contract-behavior.md       # Full behavior policy
    ├── ba-steps-intake.md            # Step: intake
    ├── ba-steps-backbone.md          # Step: backbone
    ├── ba-steps-frd.md               # Step: FRD
    ├── ba-steps-stories.md           # Step: user stories
    ├── ba-steps-srs-core.md          # Step: SRS core (Groups A/B/C)
    ├── ba-steps-srs-wireframes.md    # Step: SRS wireframes (Groups D/E)
    ├── ba-steps-srs-assembly.md      # Step: SRS assembly (Group F + merge)
    ├── ba-steps-wireframes.md        # Step: wireframe handoff
    ├── ba-steps-package.md           # Step: HTML packaging
    ├── ba-steps-status.md            # Step: status inspection
    ├── ba-skill-start.md             # Skill: lifecycle engine
    ├── ba-skill-do.md                # Skill: freeform router
    ├── ba-skill-next.md              # Skill: next step detection
    ├── ba-skill-collab.md            # Skill: collaboration + GitHub
    ├── ba-skill-notion.md            # Skill: Notion publishing
    ├── ba-impact.md                  # Change impact triage
    ├── ba-quality-rules.md           # Quality standards
    ├── ba-templates.md               # Full template catalog (inline)
    ├── ba-delegation.md              # Multi-BA governance
    ├── ba-agents.md                  # Agent delegation specs
    ├── ba-token-budget.md            # Token budget guardrails
    └── ba-lifecycle-*.md             # [deprecated] Legacy references
```

## Sử dụng nhanh

Sau khi cài đặt, nói với Kiro bằng ngôn ngữ tự nhiên:

| Bạn nói | BA-kit làm |
|---|---|
| "Tạo dự án BA mới" | Chạy intake: parse input → gap analysis → scope lock |
| "Tiếp tục dự án warehouse-rfp" | Detect next step → recommend + execute |
| "Đánh giá thay đổi: thêm audit log cho export" | Impact analysis → recommend rerun path |
| "Chuẩn bị handoff UI cho module auth" | Build wireframe constraint pack |
| "Xuất gói bàn giao" | Package → compiled HTML |

## Workflow tổng quan

```
Raw input → Intake + Gap Analysis → PROJECT-HOME.md
→ Requirements Backbone (scope lock)
→ Module artifacts: FRD / Stories / SRS / Screen Contract Plus
→ DESIGN.md + wireframe-input.md + wireframe-map.md
→ User tự tạo mockup / wireframe
→ Final SRS + HTML package
```

## Output structure

Khi chạy BA-kit, artifacts được tạo trong workspace:

```
plans/
  {slug}-{date}/
    PROJECT-HOME.md           # BA dashboard
    01_intake/intake.md       # Normalized input
    02_backbone/backbone.md   # Source of truth
    03_modules/{module}/      # FRD, stories, SRS per module
    04_compiled/              # HTML packages

designs/
  {slug}/DESIGN.md            # Project design system
```

## Defaults

| Setting | Value |
|---|---|
| Language | Vietnamese (override with English on request) |
| Mode | `hybrid` (backbone + targeted FRD + stories + selective SRS) |
| UI baseline | Shadcn UI (overridden by project DESIGN.md) |
| Date format | `YYMMDD-HHmm` |

## Yêu cầu

- **Kiro IDE** với Powers support
- Không cần dependencies bên ngoài
- Không cần MCP servers (trừ khi dùng `ba-notion` để publish lên Notion)

## Nguồn gốc

Power này được migrate từ [ba-kit](https://github.com/phamquangviet891/ba-kit) — bộ playbook BA đầy đủ hỗ trợ nhiều runtime (Claude Code, Codex, Antigravity). Power version tập trung vào Kiro IDE với steering-based architecture.

## License

MIT
