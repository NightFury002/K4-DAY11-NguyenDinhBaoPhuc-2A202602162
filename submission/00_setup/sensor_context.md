# Sensor context

- Rig: đây là ảnh fisheye nhìn từ một camera gắn trên xe; ảnh cho thấy vùng quan sát rộng quanh phần trước/bên
  của xe. Repo không có calibration hoặc tài liệu vị trí camera, nên không suy đoán chính xác độ cao, hướng lắp
  hay khoảng cách thực.
- `ego_body`: thân xe/gương hoặc phần xe gắn camera xuất hiện ở vùng thấp phía dưới ảnh trong phần lớn frame;
  đây là vùng cần đánh dấu `ignore_region` với `reason=ego_body`, không gán nhãn như một object giao thông.
- Vòng kính: ranh giới fisheye tạo thành vùng cong ở phần trên và dưới khung hình; hai polygon `lens_border`
  bao phần ngoài vòng kính. Chỉ dùng vùng nhìn thấy bên trong vòng kính, không suy diễn vật nằm ngoài biên.
