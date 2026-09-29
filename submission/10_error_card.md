# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B1 | BOX_GEOMETRY | 1 |
| center | B1 | MISSING | 5 |
| center | B1 | SPURIOUS | 16 |
| center | C0 | SPURIOUS | 2 |
| edge | B1 | SPURIOUS | 3 |
| edge | C0 | WRONG_CLASS | 1 |
| mid | B1 | MISSING | 5 |
| mid | B1 | SPURIOUS | 11 |
| mid | B1 | WRONG_CLASS | 1 |
| unknown | B4 | MISSING | 5 |

## Top defects
- SPURIOUS: 32 (ví dụ frame adasind_019560.jpg)
- MISSING: 15 (ví dụ frame adasind_258420.jpg)
- WRONG_CLASS: 2 (ví dụ frame adasind_019560.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: `SPURIOUS` chiếm nhiều nhất (32), tập trung ở block B1
	và đặc biệt zone center. Các dòng `L_only` cho thấy một phần là box thừa trong export người gán; các dòng
	`M_only` cho thấy model cũng có false positive ở cảnh đông. Không nên gán toàn bộ lỗi cho annotator vì
	`LM_noR`/`M_only` cần đối chiếu ảnh và teaching reference riêng.
- Cách sửa và ai nhận việc (`owner`): annotator rework các dòng `L_only` có bằng chứng ảnh theo R01/R02/R04;
	ai_team kiểm tra các `M_only` và điều chỉnh model/domain nếu lặp lại trên nhiều frame; qa giữ các ca chưa đủ
	bằng chứng ở trạng thái review hoặc escalate.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `findings.csv` có các dòng `r1_craft` và
	`r3_diag` với `L_only`, `M_only`, `LM_noR`; `r3_diag/local_quality_conflicts.csv` ghi conflict của
	`adasind_034080.jpg`; đối chiếu R01, R02, R04, R06 và R09. Repo hiện chưa có PNG/JPG trong
	`submission/screenshots/`, nên cần bổ sung ảnh chụp thật trước khi nộp chính thức.
