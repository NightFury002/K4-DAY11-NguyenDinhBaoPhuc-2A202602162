# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `adasind_034080.jpg` | 6 ca L thiếu/thừa hoặc hình học, gồm 2 missing và 4 spurious | Có nhiều xung đột nhất trong slice; cần tách lỗi box thật khỏi ảnh hưởng ignore và kiểm lại các vật gần mép | Ảnh gốc, `r3_diag/local_quality_conflicts.csv`, overlay compare, rule R01/R02/R06/R09 |
| `adasind_014670.jpg` | 5 ca L spurious và 1 missing; có một khác class Bus/Truck | Số box thừa cao và có class phương tiện dễ nhầm, phù hợp review trước khi sửa guideline | Ảnh gốc, `compare.html`, conflict CSV, rule R04 và decision log |

Giới hạn của kết luận từ ba frame ADASIND: đây chỉ là ba frame của một camera fisheye, không đại diện cho
bốn camera SVM, các điều kiện thời gian, thời tiết, tốc độ hay seam. Các số quality đo độ khớp với teaching
reference nhỏ này, không phải tỷ lệ lỗi sản xuất hay gold set.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: kiểm đủ tám
ô `camera_id × slice_type`, phân bố mẫu theo các block thời gian và tránh lấy liên tiếp một cảnh làm nhiều
ca độc lập. Sau đó review riêng normal/hard, kiểm độ phủ theo camera và seam. Kế hoạch chỉ tạo mẫu có chủ đích
để phát hiện ca khó; không có frame-level ground truth, sampling weights hoặc quy trình đánh giá độc lập nên
không dùng để ước lượng tỷ lệ lỗi.
