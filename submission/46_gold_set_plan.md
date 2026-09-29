# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Xe/người ở seam trước, xe cắt mép, vật gần nhau | Méo fisheye và chồng lấn làm sai box/class | Calibration trước, hướng nhìn, vùng hợp lệ và quy ước box trên ảnh gốc | Hai reviewer độc lập, adjudicator giải quyết bất đồng và kiểm lại ảnh gốc trước khi khóa |
| rear | Vật nhỏ trong vùng lùi, che khuất, ánh sáng ngược | Recall thấp khi vật sát mép hoặc bị xe khác che | Calibration sau, biên ảnh, occlusion/truncation và timestamp | Review độc lập theo normal/hard, lấy mẫu lại ca bất đồng trước khi gọi gold |
| left | Seam trước-trái, xe hai bánh/người dắt xe, vật méo ở rìa | Dễ nhầm rider với Pedestrian/Bike và gộp hai vật | Calibration trái, vùng seam, rule rider và ignore region | Một reviewer gán, reviewer thứ hai kiểm mù, adjudicator ghi quyết định và lý do |
| right | Seam sau-phải, vật chồng lấn, object ra/vào khung | Perspective khác và Outside dễ làm đứt track | Calibration phải, timestamp, policy Outside/keyframe và vùng giao nhau | Soát từng hard case bằng ảnh đồng bộ; chỉ khóa sau khi giải quyết mọi bất đồng |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): refresh khi đổi vị trí/thông số camera,
	calibration hoặc phiên bản guideline; cũng refresh khi drift dữ liệu, xuất hiện class mới, hoặc review phát
	hiện nhóm hard case chưa có trong gold.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: cần timestamp đồng bộ, calibration
	giữa hai camera, tọa độ/độ tin cậy tương ứng và policy output quy định giữ, hợp nhất hoặc để hai box. Không
	tự xóa một box chỉ vì hai ảnh nhìn cùng vật.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera:
	chúng chỉ đo sự đồng thuận hoặc độ khớp trên một camera và tập frame giới hạn; không kiểm tra được khác biệt
	về vị trí lắp, seam, calibration, tracking và phân bố hard case của ba camera còn lại.
