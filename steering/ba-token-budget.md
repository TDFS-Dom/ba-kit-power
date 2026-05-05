---
inclusion: manual
---

# BA-kit Token Budget

Guardrail cho instruction surface. Dùng để kiểm soát context window khi load steering files.

## Nguyên tắc
- Đơn vị: bytes (ổn định hơn tokenization)
- Các ngưỡng `max` là guardrail, không phải mục tiêu lấp đầy
- Khi mở rộng instruction surface → cập nhật baseline + max

## Steering Load Strategy cho Power

Vì Power dùng steering files (load on-demand), áp dụng:

1. **Always-loaded** (ba-contract.md, ba-routing.md): ~3KB mỗi file — luôn trong context
2. **On-demand steps**: chỉ load steering file tương ứng khi command active
3. **Never load all steps cùng lúc** — mỗi command chỉ cần 1-2 step files

## Recommended Load Bundles

| Workflow | Load files | Est. size |
|---|---|---|
| Intake | ba-contract + ba-steps-intake | ~6KB |
| Backbone | ba-contract + ba-steps-backbone | ~5KB |
| FRD | ba-contract + ba-steps-frd | ~4KB |
| Stories | ba-contract + ba-steps-stories | ~4KB |
| SRS Core | ba-contract + ba-steps-srs-core | ~7KB |
| SRS Full | ba-contract + srs-core + srs-wireframes + srs-assembly | ~12KB |
| Wireframes | ba-contract + ba-steps-wireframes | ~7KB |
| Package | ba-contract + ba-steps-package | ~4KB |
| Impact | ba-contract + ba-impact (existing) | ~5KB |
| Routing | ba-routing (always loaded) | ~2KB |

## Khi budget tight
1. Gỡ rule trùng lặp
2. Tách step file nếu phình quá nhanh
3. Đưa phần deterministic sang machine-readable thay vì prose
