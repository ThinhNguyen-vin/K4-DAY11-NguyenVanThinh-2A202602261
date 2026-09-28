# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Hai đoạn sơn ở
	vùng tiền cảnh giữa ảnh, một đoạn chạy từ khoảng (279,518) đến (422,554)
	và một đoạn kế bên chạy từ khoảng (399,517) đến (574,544). Đây là các vạch
	phân cách nhìn thấy giữa những ô đỗ liền nhau; các đoạn sơn khác cùng hàng
	cũng được giữ lại khi chúng tiếp tục thể hiện ranh giới ô.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Không gán nhãn các mép
	của dải lối xe chạy ở vùng xa và các đường biên ở sát mép ảnh. Chúng chỉ thể
	hiện mép đường/lối di chuyển hoặc bị cắt bởi khung hình, không đủ bằng chứng
	để coi là ranh giới của một ô đỗ riêng lẻ.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Polygon bao phủ
	dải mặt đường trống nhìn thấy ở phần dưới và giữa ảnh, phía trước hàng ô đỗ;
	nó dừng tại mép ảnh và các mép vùng nhìn thấy, không đi xuyên qua xe, curb
	hoặc vùng bị che. Đây là vùng trống quan sát được trên ảnh tĩnh, không phải
	kết luận về khả năng lái xe an toàn.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): không có.
