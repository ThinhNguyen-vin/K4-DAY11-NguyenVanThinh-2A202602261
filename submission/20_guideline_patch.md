# Guideline patch

- **Rule mới đề xuất:** **R12 — Không rework nhãn người chỉ vì model bất đồng.** Với cell
	`LR_noM` hoặc `M_only`, phải kiểm tra ảnh fisheye gốc và ghi `why`, `evidence`,
	`owner` và `action` trong `findings.csv`. Nếu người gán nhãn và teaching reference
	cùng thống nhất, giữ nhãn người bằng `keep_with_reason`; chỉ rework khi có bằng
	chứng trực tiếp từ ảnh và rule gán nhãn.
- **Áp dụng cho:** Các bất đồng người–reference–model trong P4, đặc biệt `M_only`
	và `LR_noM` ở zone `mid`/`edge`; liên quan đến box, class, ngưỡng H=40 và hình
	học fisheye. Không dùng rule này để bỏ qua lỗi `ego_body`, `lens_border` hoặc
	thuộc tính đã thấy rõ trên ảnh.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R01–R09 quy định cách
	gán box, class, attribute và ignore trên ảnh, nhưng chưa quy định cách phân xử
	khi model khác cả người và reference. Slice B4-edge có nhiều model thừa/thiếu,
	trong khi local-quality của bản người là `TP=20`, `FP=0`, `FN=0`; nếu sửa theo
	model một cách máy móc sẽ làm mất nhãn phù hợp với ảnh.
- **`rules_version` mới:** `v1.1.0`
- **Hiệu lực từ:** P4 `r3_diag`, sau khi hoàn tất QA mù và trước khi quyết định
	rework.
