# Sensor context

- **Slice:** `B4-edge`, gồm các frame `adasind_236370.jpg`, `adasind_258420.jpg` và
  `adasind_310008.jpg`.
- **Rig:** Đây là một camera fisheye đơn hướng về phía trước, có vẻ được gắn trên
  xe và nhìn ra mặt đường cùng các phương tiện phía trước. Vị trí gắn chính xác và
  thông số camera không được suy ra thêm từ ảnh.
- **`ego_body`:** Có phần thân/nắp xe tối màu ở vùng đáy khung hình, nằm phía dưới
  vùng nhìn đường và thay đổi theo phối cảnh giữa các frame. Không nhận ra rõ vô
  lăng hoặc gương trong ba frame này.
- **Vòng kính:** Vùng nhìn fisheye là một vòng tròn lớn, tâm xấp xỉ ở giữa ảnh và
  hơi lệch xuống (khoảng y=940–1040 trên ảnh 1080x1920), bán kính khoảng 800–820
  pixel. Phần ảnh nằm trong vòng kính chiếm khoảng 75–80% khung hình; vành đen
  nằm rõ ở mép trên, mép dưới và các góc bên ngoài vòng.
