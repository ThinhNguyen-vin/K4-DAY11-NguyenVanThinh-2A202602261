# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B4 | MISSING | 2 |
| center | B4 | SPURIOUS | 2 |
| center | C0 | MISSING | 1 |
| center | C0 | SPURIOUS | 1 |
| edge | B4 | MISSING | 1 |
| edge | B4 | SPURIOUS | 1 |
| edge | C0 | WRONG_CLASS | 1 |
| mid | B4 | MISSING | 3 |
| mid | B4 | SPURIOUS | 8 |
| mid | C0 | MISSING | 1 |

## Top defects
- SPURIOUS: 12 (ví dụ frame adasind_019560.jpg)
- MISSING: 8 (ví dụ frame adasind_019560.jpg)
- WRONG_CLASS: 1 (ví dụ frame adasind_019560.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Lỗi nổi bật là `SPURIOUS` của model, đặc biệt ở zone `mid` của block B4 (8 ca `M_only`) và các ca `MISSING` `LR_noM`. Đây là giả thuyết `E4_model_domain`: model có thể nhạy sai với méo fisheye, vật nhỏ/nhiều vật gần nhau và miền ảnh khác dữ liệu huấn luyện. Không quy kết đây là lỗi người vì `local_quality` cho export đã khóa đạt `TP=20, FP=0, FN=0`, mean IoU `0.852`.
- Cách sửa và ai nhận việc (`owner`): Giữ nguyên annotation của người khi người và teaching reference cùng thấy vật; không rework chỉ vì model khác. Giao `ai_team` kiểm tra model trên thêm frame fisheye và điều chỉnh dữ liệu/threshold nếu cần. Các ca còn chưa đủ bằng chứng phải đối chiếu ảnh gốc trước khi thay đổi nhãn.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `submission/r3_diag/model_compare.md` ghi các ca `M_only` và `LR_noM`; `submission/r3_diag/zone_table.md` cho thấy `mid` có 3 model thiếu và 8 model thừa; `submission/r3_diag/local_quality.md` ghi `TP=20`, `FP=0`, `FN=0`. Các dòng tương ứng nằm trong `findings.csv` với `why=E4_model_domain`, `owner=ai_team`, `action=keep_with_reason`; đối chiếu theo R01/R02 và giới hạn taxonomy E4.
