# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_019560.jpg
- L2+R3 edge WRONG_CLASS
- L4 center SPURIOUS
- L5 center SPURIOUS

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 3 | 3 | 0 | 2 |
| mid | 2 | 2 | 0 | 0 |
| edge | 1 | 0 | 1 | 1 |

## Nhận xét

- Ở frame `adasind_019560.jpg`, box `L2` và `R3` cùng trỏ tới một vật ở vùng `edge` nhưng khác class (`WRONG_CLASS`). Cần mở ảnh gốc và đối chiếu rule phân biệt class trước khi quyết định nhãn nào đúng.
- Hai box `L4` và `L5` ở vùng `center` là `SPURIOUS`: chúng xuất hiện trong nhãn L nhưng không có box tương ứng trong reference R. Cần kiểm tra lại vật thể trên ảnh, chiều cao tối thiểu và phạm vi `ignore_region` trước khi sửa.
- Theo zone, `center` có 2 spurious nhưng không thiếu box; `mid` khớp hoàn toàn; `edge` có 1 missing và 1 spurious. Vì đây chỉ là một frame calibration, chưa đủ bằng chứng để kết luận lỗi tập trung ở vùng méo rìa hay do gán nhãn.
- Hành động tiếp theo: xem `compare.html` cùng ảnh gốc, ghi từng ca vào `submission/findings.csv` với bằng chứng và nguyên nhân sau khi kiểm tra; không xem teaching reference là chân lý tuyệt đối nếu ảnh và guideline cho thấy điều ngược lại.
