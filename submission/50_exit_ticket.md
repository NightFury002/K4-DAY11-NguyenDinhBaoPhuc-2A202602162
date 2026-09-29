# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? Đây không mặc định là `DUPLICATE`: cùng một vật ở seam có thể hợp lệ xuất hiện trên
   hai camera. Cần rule riêng về seam để quyết định giữ hai box, hợp nhất ở BEV hoặc chuyển cho tầng output;
   chỉ gọi duplicate khi policy đích yêu cầu một biểu diễn duy nhất và có đủ calibration/timestamp.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Giữ cùng track ID khi cùng vật còn quan sát được và hình học/identity liên tục; thêm keyframe khi
   hình dạng hoặc vị trí thay đổi đáng kể; dùng Outside khi vật ra khỏi vùng nhìn theo guideline. Trước khi
   nối track qua hai camera cần timestamp đồng bộ, calibration, vùng seam tương ứng và policy identity/output.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Ở `adasind_034080.jpg`, các
   conflict quanh `L2`, `L6`, `L9`, `L11` và các box missing cho thấy cần phân biệt box thừa với vùng ignore
   trước khi kết luận. Tôi giữ bằng chứng ảnh/CSV, ghi finding và không tự sửa theo một con số quality; nếu làm
   lại, tôi sẽ quét thiếu box theo R01 sau khi kiểm class và ignore ở từng frame.
