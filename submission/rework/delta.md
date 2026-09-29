# Rework delta

| zone | matched before | matched after | missing before | missing after | spurious before | spurious after |
|---|---:|---:|---:|---:|---:|---:|
| center | 5 | 5 | 2 | 2 | 5 | 5 |
| mid | 10 | 10 | 1 | 1 | 3 | 3 |
| edge | 2 | 2 | 0 | 0 | 1 | 1 |

## Findings action=rework
- adasind_014670.jpg L2 SPURIOUS: chưa sửa
- adasind_014670.jpg L5 SPURIOUS: chưa sửa
- adasind_014670.jpg R5 MISSING: chưa sửa
- adasind_032280.jpg L2 SPURIOUS: chưa sửa
- adasind_032280.jpg L5 SPURIOUS: chưa sửa
- adasind_034080.jpg L2 SPURIOUS: chưa sửa
- adasind_034080.jpg L6 SPURIOUS: chưa sửa
- adasind_034080.jpg L9 SPURIOUS: chưa sửa
- adasind_034080.jpg L11 SPURIOUS: đã sửa
- adasind_034080.jpg R2+M3 MISSING: chưa sửa
- adasind_034080.jpg R9 MISSING: chưa sửa

## Kết luận

- Kết quả trước và sau không thay đổi ở cả ba zone: center vẫn có 2 missing và 5 spurious, mid vẫn có 1
	missing và 3 spurious, edge vẫn có 1 spurious.
- Chỉ một finding (`adasind_034080.jpg`, `L11`, `SPURIOUS`) được ghi nhận là đã sửa; việc này chưa làm thay
	đổi các số tổng hợp theo zone, nên chưa có bằng chứng rằng chất lượng đã cải thiện.
- Các finding còn lại được giữ nguyên vì chưa hoàn tất sửa/kiểm trên ảnh hoặc chưa đủ căn cứ để thay đổi nhãn.
	Không chỉnh tay các số trong bảng; nếu tiếp tục rework, cần sửa trong CVAT, export bản mới, khóa lại rồi
	chạy lại lệnh `rework`.
- Bước tiếp theo: QA kiểm lại ảnh của các ca còn `chưa sửa`, ưu tiên các ca `MISSING`/`SPURIOUS` ở center và
	mid; ca chưa phân xử cần được giữ ở trạng thái escalate thay vì sửa đoán.
