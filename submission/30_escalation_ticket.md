# Escalation ticket

## Ticket 1

- **Frame:** `B4-edge` — ưu tiên các ca `M_only` ở `adasind_258420.jpg`
	(đặc biệt zone `mid`) và các ca `LR_noM` cùng slice.
- **Ảnh chụp:** `submission/screenshots/model_compare.png` và
	`submission/screenshots/qa_overlay.png`; bảng/overlay gốc ở
	`submission/r3_diag/model_compare.html` và `zone_table.md`.
- **Expected impact:** Model có thể phát hiện thừa hoặc bỏ sót vật trên ảnh
	fisheye, nhất là zone `mid`; nếu dùng model làm chuẩn để sửa nhãn người,
	annotation đúng có thể bị thay đổi sai. Trong slice này có 3 ca model thiếu và
	8 ca model thừa ở `mid`, trong khi local-quality của bản người là `TP=20`,
	`FP=0`, `FN=0`.
- **Owner:** `ai_team`
- **Recommendation:** Giữ nhãn người khi người và teaching reference cùng
	thống nhất; không rework chỉ vì `M_only`/`LR_noM`. Kiểm tra thêm nhiều frame
	fisheye ở các zone, rà ngưỡng và chất lượng model, rồi đánh giá lại trước khi
	dùng output model cho hỗ trợ gán nhãn. Nếu cần báo cáo sản phẩm, mở escalation
	sau khi có mẫu rộng hơn vì slice này chỉ gồm 3 frame của một camera.
