# Tự soát

- Cảnh báo parser: CVAT job export không ghi tên task; đã xác nhận tên task trên CVAT là `Day11 · ADASIND · B4-edge · raw_fisheye`.

## Checklist thủ công
- [x] Phạm vi H=40 và vật cần vẽ
- [x] lens_border và ego_body
- [x] Class sáu nhãn
- [x] Rider và Bike
- [x] Geometry trên ảnh fisheye gốc
- [x] truncated và occluded
- [x] Vật thiếu hoặc box trùng
- [x] ignore_region có reason
- [x] Tên task raw_fisheye và export CVAT 1.1

## Fill ratio (K12)
- adasind_236370.jpg box 3 edge: 0.694
- adasind_236370.jpg box 5 center: 0.776
- adasind_310008.jpg box 4 edge: 0.486
- adasind_310008.jpg box 3 edge: 0.551
mean edge: 0.577 (n=3)
mean center: 0.776 (n=1)
