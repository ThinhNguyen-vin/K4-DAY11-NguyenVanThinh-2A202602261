# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó
   chưa nên tự gọi là `DUPLICATE`; cần một quy tắc seam riêng. Hai box có thể là
   hai quan sát hợp lệ của cùng vật. Chỉ hợp nhất, giữ cả hai hoặc chọn một khi
   có timestamp đồng bộ, calibration/extrinsic, bằng chứng hình học cho cùng vật
   và policy output đã quy định. Thiếu các điều kiện đó thì giữ annotation theo
   từng camera và escalate.
2. Một vật đi qua nhiều frame trên cùng camera được giữ cùng track ID khi
   identity còn nhất quán qua vị trí, hình dạng, appearance và timestamp. Thêm
   keyframe khi hình học hoặc trạng thái thay đổi đáng kể; ghi `Outside` khi vật
   ra khỏi trường nhìn thay vì kéo box vào vùng không thấy. Trước khi nối track
   qua hai camera cần timestamp đồng bộ, calibration/extrinsic, vùng overlap,
   bằng chứng appearance/hình học và policy xử lý identity ở seam; không tự nối
   chỉ vì hai box gần nhau.
3. Ở C0, ca `adasind_019560.jpg` `L5+R3` được ghi là `WRONG_CLASS` trong
   `findings.csv`; đây là chỗ cần đối chiếu ảnh gốc, rule class/rider và teaching
   reference thay vì bảo vệ nhãn theo cảm giác. Với slice B4-edge, các ca model
   `M_only` và `LR_noM` được giữ theo nhãn người khi người và reference thống
   nhất, vì `local_quality` đạt `TP=20`, `FP=0`, `FN=0`; bất đồng được ghi là
   `E4_model_domain` và escalate cho `ai_team`. Nếu làm lại, mình sẽ kiểm class
   rider/ThreeWheeler và `ego_body` trước khi export, sau đó ghi evidence và
   group K12 ngay trong vòng tự soát thay vì chờ cuối quy trình.
