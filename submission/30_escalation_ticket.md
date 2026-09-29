# Escalation ticket

## Ticket 1

- **Frame:** `adasind_034080.jpg`, các conflict `missing_annotation` và `extra_annotation` trong
	`r3_diag/local_quality_conflicts.csv`.
- **Ảnh chụp:** Chưa có PNG/JPG trong `submission/screenshots/`; giữ `local_quality_conflicts.csv` và
	`r3_diag/model_compare.html` làm bằng chứng có thể mở lại, bổ sung ảnh chụp trước khi nộp chính thức.
- **Expected impact:** Có thể làm sai recall/precision và làm người review nhầm giữa thiếu box, box thừa và
	khác biệt do vùng ignore; ảnh hưởng quyết định rework nếu không xem lại ảnh gốc.
- **Owner:** qa
- **Recommendation:** QA chụp overlay và ảnh gốc của hai conflict này, annotator xác minh theo R01–R09; nếu
	vẫn bất đồng thì guideline owner quyết định trước khi dùng ca làm ví dụ hoặc đưa vào gold set.
