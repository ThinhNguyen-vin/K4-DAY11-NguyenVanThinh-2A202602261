# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Vật nhỏ ở xa, xe/người bị che, ánh sáng ngược, seam trước-trái và trước-phải | Fisheye làm méo rìa; vật nhỏ dễ dưới H; vùng seam có thể xuất hiện trên hai camera | Giữ ảnh gốc, timestamp, camera ID, calibration nội tại và extrinsic; ghi polygon lens/ego nếu policy yêu cầu | Hai annotator độc lập; adjudicator xem ảnh gốc và overlay; kiểm box, class, attribute và track trước khi chốt |
| rear | Xe tiến gần, đèn pha hoặc ánh sáng yếu, vật bị che bởi xe lớn, seam góc sau | Tương phản thay đổi và vật bị cắt khi ra vào trường nhìn; tracking dễ mất identity | Giữ timestamp liên tục, calibration và hướng trục camera; ghi trạng thái Outside khi vật ra khỏi view | Review độc lập theo đoạn thời gian; đối chiếu frame trước/sau và adjudicate mọi ca mất track hoặc cắt biên |
| left | Xe máy/người sát thân xe, curb, vật ở rìa cong, seam trước-trái/sau-trái | Góc nhìn ngang làm box méo; ego body có thể che vật; dễ nhầm vật tĩnh với object động | Giữ mask ego body, lens border, calibration và tọa độ vùng overlap; không tự nắn ảnh trước khi gán nhãn | Một lượt box/class và một lượt geometry/attribute; người thứ ba phân xử ca bị che hoặc nằm trong seam |
| right | Xe sát xe, xe ba bánh/xe máy đông, ánh sáng chói, seam trước-phải/sau-phải | Vật gần chiếm diện tích lớn và dễ chồng box; vùng ngoài cùng bị méo/cắt; cross-camera duplicate dễ xảy ra | Giữ ảnh gốc, timestamp, calibration, vùng overlap và policy output; tách ego body khỏi object giao thông | Hai annotator độc lập; kiểm duplicate theo timestamp và calibration trước khi hợp nhất hoặc giữ hai box |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): Refresh khi
	đổi camera hoặc calibration, thay đổi policy seam/tracking, đổi taxonomy hoặc
	threshold H/attribute, phát hiện drift theo thời gian/ánh sáng, hoặc tỷ lệ bất
	đồng vượt ngưỡng đã thống nhất. Giữ phiên bản cũ để truy nguyên thay vì ghi đè.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: Cần
	cùng timestamp hoặc đồng bộ thời gian, calibration/extrinsic đã xác nhận,
	bằng chứng vật lý cho thấy hai box là cùng một vật và policy quy định output
	là hợp nhất, giữ cả hai hay chọn một box. Nếu thiếu một điều kiện, giữ hai
	annotation theo camera và escalated thay vì tự ghép hoặc xóa.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh
	gold set đúng cho cả bốn camera: Hai người có thể cùng mắc một lỗi hoặc cùng
	đọc sai một teaching reference; một camera không đại diện cho méo, ánh sáng,
	ego body và seam của ba camera còn lại. Gold set cần nhiều camera, ca normal và
	hard, adjudication độc lập, calibration/tracking evidence và phiên bản policy
	rõ ràng.
