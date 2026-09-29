# Guideline patch

- **Rule mới đề xuất:** R12 — Sau khi rà từng box, phải quét lại toàn bộ frame để tìm object nhìn thấy cao
	`H >= 40 px` nhưng chưa có box; trong cảnh đông, ghi riêng từng object theo vị trí tương đối và không gộp
	nhiều vật vào một box.
- **Áp dụng cho:** Mọi class object trong vùng hợp lệ, đặc biệt `Bike`, `Pedestrian` và các frame dense/edge.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R01 đã nêu ngưỡng chiều cao nhưng chưa quy định
	một lượt quét thiếu nhãn độc lập sau khi vẽ. QA dễ chỉ kiểm các box đang có và bỏ sót vật nhỏ nằm cạnh vật
	lớn hoặc gần mép ảnh.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** P3 QA và mọi vòng gán nhãn sau P3.
