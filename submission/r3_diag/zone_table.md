# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 7 | 2 | 5 | 3 | 7 | SPURIOUS (4) |
| mid | 11 | 1 | 3 | 5 | 7 | SPURIOUS (2) |
| edge | 2 | 0 | 1 | 0 | 1 | SPURIOUS (1) |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: `center` có nhiều lỗi tuyệt đối nhất:
	L missing=2, L spurious=5, M missing=3 và M thừa=7; lỗi L chính là SPURIOUS (4). `mid` đứng sau với L
	missing=1, L spurious=3, M missing=5 và M thừa=7. `edge` ít ca nhất nhưng vẫn có 1 L spurious và 1 M thừa.
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: center có
	nhiều vật cùng lúc nên dễ gán box thừa hoặc tách/gộp sai; mid có thể chịu ảnh hưởng của méo và vật chồng lấn.
	Đây chỉ là giả thuyết cần kiểm trên ảnh, không suy nguyên nhân từ zone. Ba frame của một camera không đủ đại
	diện cho bốn camera, mọi khoảng cách, thời tiết hoặc seam cross-camera.
