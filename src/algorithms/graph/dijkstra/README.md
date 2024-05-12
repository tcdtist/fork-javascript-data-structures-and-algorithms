# Thuật toán Dijkstra

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

Thuật toán Dijkstra là một thuật toán dùng để tìm đường đi ngắn nhất
giữa các nút trong một đồ thị, ví dụ như mạng lưới đường bộ.

Thuật toán này có nhiều biến thể; biến thể gốc của Dijkstra
tìm đường đi ngắn nhất giữa hai nút, nhưng một biến thể phổ biến hơn
đặt một nút duy nhất là nút "nguồn" và tìm
đường đi ngắn nhất từ nút nguồn đến tất cả các nút khác trong đồ thị,
tạo ra một cây đường đi ngắn nhất.

![Dijkstra](https://upload.wikimedia.org/wikipedia/commons/5/57/Dijkstra_Animation.gif)

Thuật toán Dijkstra để tìm đường đi ngắn nhất giữa `a` và `b`.
Nó chọn nút chưa được thăm có khoảng cách thấp nhất,
tính toán khoảng cách thông qua nó đến mỗi láng giềng chưa được thăm,
và cập nhật khoảng cách của láng giềng nếu nhỏ hơn. Đánh dấu đã thăm
(đặt thành màu đỏ) khi hoàn thành với các láng giềng.

## Tham khảo

- [Wikipedia](https://vi.wikipedia.org/wiki/Thu%E1%BA%ADt_to%C3%A1n_Dijkstra)
- [Trên YouTube bởi Nathaniel Fan](https://www.youtube.com/watch?v=gdmfOwyQlcI&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [Trên YouTube bởi Tushar Roy](https://www.youtube.com/watch?v=lAXZGERcDf4&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
