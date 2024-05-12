# Thuật toán Bellman–Ford

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

Thuật toán Bellman–Ford là một thuật toán tính toán đường đi ngắn nhất
từ một đỉnh nguồn đơn lẻ đến tất cả các đỉnh khác
trong một đồ thị có hướng có trọng số. Nó chậm hơn thuật toán Dijkstra
đối với cùng một vấn đề, nhưng linh hoạt hơn, vì nó có khả năng
xử lý đồ thị trong đó một số trọng số cạnh là số âm.

![Bellman-Ford](https://upload.wikimedia.org/wikipedia/commons/2/2e/Shortest_path_Dijkstra_vs_BellmanFord.gif)

## Độ phức tạp

Hiệu suất trường hợp tồi nhất `O(|V||E|)`
Hiệu suất trường hợp tốt nhất `O(|E|)`
Độ phức tạp không gian trường hợp tồi nhất `O(|V|)`

## Tham khảo

- [Wikipedia](https://vi.wikipedia.org/wiki/Thu%E1%BA%ADt_to%C3%A1n_Bellman%E2%80%93Ford)
- [Trên YouTube bởi Michael Sambol](https://www.youtube.com/watch?v=obWXjtg0L64&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
