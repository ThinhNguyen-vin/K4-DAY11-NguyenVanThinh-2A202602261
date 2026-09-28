# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `B4/mid`: `adasind_236370.jpg`, `adasind_258420.jpg`, `adasind_310008.jpg` | 11 ca model bất đồng: 3 `LR_noM` và 8 `M_only`; tập trung ở `adasind_258420.jpg` | Đây là zone có nhiều model thiếu/thừa nhất; cần kiểm tra vật nhỏ, nhiều vật gần nhau và khả năng model lệch miền fisheye trước khi đề xuất rework nhãn người. | `submission/r3_diag/model_compare.md`, `zone_table.md`, `local_quality_conflicts.csv`, ảnh gốc ba frame |
| `B4/edge`: `adasind_236370.jpg`, `adasind_258420.jpg`, `adasind_310008.jpg` | 2 ca model bất đồng: 1 `LR_noM` và 1 `M_only` | Rìa vòng kính dễ méo/cắt; cần kiểm tra `truncated`, box bám phần nhìn thấy, `lens_border` và không nhầm rider với Pedestrian. | `submission/r3_diag/model_compare.html`, `local_quality.md`, `r1_craft/selfqc.md`, ảnh gốc và overlay QA |

Giới hạn của kết luận từ ba frame ADASIND: đây là một slice ba frame của một camera,
teaching reference chưa phải gold set và số ca model không phải tỷ lệ lỗi đại diện.
Kết luận chỉ dùng để ưu tiên review và tạo giả thuyết; cần thêm frame, camera và
người soát độc lập trước khi khẳng định nguyên nhân hoặc thay đổi model.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv`: chia đều 25 frame cho
mỗi ô `front/rear/left/right × normal/hard`, lấy mẫu rải theo thời gian thay vì
chọn nhiều frame liên tiếp cùng một cảnh. Mỗi camera cần có hard case về seam,
méo rìa, che khuất, ánh sáng và vật nhỏ; normal dùng để kiểm tra nền phân bố.
Review hai lượt: người thứ nhất gán nhãn, người thứ hai soát độc lập trên ảnh
gốc; chỉ sau khi thống nhất mới tạo reference. Bảng 200 frame chỉ giúp tìm và
ưu tiên ca khó, không đo được tỷ lệ lỗi của 50.000 frame vì không có sampling
frame-level ngẫu nhiên đã hiệu chỉnh, không có calibration/track đầy đủ và chưa
có gold set được nhiều người xác nhận.
