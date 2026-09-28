# QA review · B4-edge

Mã khóa: 3F39-D847

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_236370.jpg | L1 Bike | R03 | Box bao cả xe hai bánh và người lái; giữ một box Bike, không tách rider thành Pedestrian. |
| adasind_236370.jpg | L2 Car, L5 Truck | R04 | Kiểm tra lại class theo hình dạng xe; L2 ở rìa trái bị cắt nên cần giữ truncated nếu phần xe chạm biên/vòng kính. |
| adasind_236370.jpg | L3 Bike, L4/L6/L7 Pedestrian | R01/R02 | Các vật đủ ngưỡng H và box bám phần nhìn thấy; soát riêng các box người gần xe để không gộp nhầm người đi bộ với rider. |
| adasind_258420.jpg | L2/L3/L6 ThreeWheeler | R04 | Các xe ba bánh được giữ đúng class ThreeWheeler, không đổi thành Car/Truck/Bus. |
| adasind_258420.jpg | L1/L7 Bike, L4/L8 Pedestrian | R03 | Kiểm tra rider: người ngồi trên xe hai bánh phải nằm trong box Bike; Pedestrian chỉ giữ khi là người đi bộ tách biệt. |
| adasind_310008.jpg | L1-L4 Pedestrian | R01/R02 | Có nhiều người gần nhau và box chồng lấn; đối chiếu ảnh gốc để bảo đảm mỗi box là một người thật, không phải box trùng. |
| adasind_310008.jpg | L5 ThreeWheeler | R04 | Xe ba bánh ở vùng giữa ảnh được gán đúng ThreeWheeler; box bám phần xe nhìn thấy. |

Kết luận QA: chưa thấy lỗi chắc chắn cần sửa chỉ từ overlay; các điểm nêu trên cần được đối chiếu trực tiếp với ảnh gốc trước khi quyết định giữ hoặc rework. Các nhận xét này là cold review trước khi mở reference/model.
