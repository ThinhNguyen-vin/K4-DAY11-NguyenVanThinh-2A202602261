# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 4 | 0 | 0 | 2 | 2 | — |
| mid | 9 | 0 | 0 | 3 | 8 | — |
| edge | 7 | 0 | 0 | 1 | 1 | — |

## Nhận xét

- Người (L) không có ca thiếu hoặc thừa ở cả ba zone: `L missing = 0` và `L spurious = 0`. Sai lệch tập trung ở model (M), nhiều nhất tại zone `mid` với 11 ca (`3 M missing` và `8 M thừa`), tiếp theo là `center` với 4 ca và `edge` với 2 ca. Vì vậy không nên kết luận người gán nhãn sai chỉ từ các số này.
- Mức M thừa và M thiếu ở `mid` có thể liên quan đến độ méo fisheye, vật nhỏ/nhiều vật gần nhau và ngưỡng hoặc box model chưa ổn định trong miền ADASIND; cần đối chiếu từng frame trong `model_compare.html` và `local_quality_conflicts.csv`. Đây chỉ là giả thuyết, không phải kết luận nguyên nhân. Slice `B4-edge` chỉ có 3 frame và một camera, nên không đại diện cho toàn bộ 48 frame hay bốn camera SVM; các số này không phải chứng nhận chất lượng model.
