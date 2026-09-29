# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Vạch trắng dọc bị cắt ở mép dưới bên trái ảnh và vạch trắng xiên lớn ở khu vực tiền cảnh phía dưới, hơi lệch trái trung tâm. Cả hai đều là phần sơn nhìn thấy dùng để phân chia các ô đỗ; polyline chỉ bám theo phần nhìn thấy và không nối qua vùng khuất.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Dải sáng mảnh chạy ngang ở khu vực xa phía trên ảnh không được vẽ vì không đủ rõ đây là ranh giới của một ô đỗ riêng lẻ; có thể là mép hoặc vạch dẫn hướng của lối xe chạy.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Polygon bao phần mặt đường/lối xe chạy trống giữa các dãy ô, dừng tại các vạch phân chia ô và mép ảnh; không đi xuyên qua các vạch, xe hoặc vật cản. Vùng bị che bởi các dấu sơn và mép khuất không được suy đoán thêm.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): Không có. Dấu sáng ở xa đã được loại vì không đủ bằng chứng để xác định là `parking_line`.
