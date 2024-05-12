# Thuật toán Kruskal - Kruskal's Algorithm

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

Thuật toán Kruskal là một thuật toán cây khung nhỏ nhất, tìm cạnh có trọng số nhỏ nhất có thể nối hai cây trong rừng. Đây là một thuật toán tham lam trong lý thuyết đồ thị khi nó tìm một cây khung nhỏ nhất cho một đồ thị có trọng số và liên thông, thêm các cung có chi phí tăng dần ở mỗi bước. Điều này có nghĩa là nó tìm một tập hợp các cạnh tạo thành một cây bao gồm mọi đỉnh, nơi tổng trọng số của tất cả các cạnh trong cây được tối thiểu hóa. Nếu đồ thị không liên thông, thì nó tìm một rừng khung nhỏ nhất (một cây khung nhỏ nhất cho mỗi thành phần liên thông).

![Kruskal Algorithm](https://upload.wikimedia.org/wikipedia/commons/5/5c/MST_kruskal_en.gif)

![Kruskal Demo](https://upload.wikimedia.org/wikipedia/commons/b/bb/KruskalDemo.gif)

Một mô phỏng cho thuật toán Kruskal dựa trên khoảng cách Euclid.

## Cây Khung Nhỏ Nhất - Minimum Spanning Tree

Một **cây khung nhỏ nhất** (MST) hay cây khung có trọng số nhỏ nhất là một tập hợp các cạnh của một đồ thị liên thông, có trọng số cạnh, (không) có hướng nối tất cả các đỉnh lại với nhau, không có chu trình và có tổng trọng số cạnh nhỏ nhất có thể. Nói cách khác, đó là một cây khung mà tổng trọng số của các cạnh là nhỏ nhất có thể. Một cách tổng quát hơn, bất kỳ đồ thị có trọng số cạnh không có hướng (không nhất thiết phải liên thông) đều có một rừng khung nhỏ nhất, là sự kết hợp của các cây khung nhỏ nhất cho các thành phần liên thông của nó.

![Minimum Spanning Tree](https://upload.wikimedia.org/wikipedia/commons/d/d2/Minimum_spanning_tree.svg)

Một đồ thị phẳng và cây khung nhỏ nhất của nó. Mỗi cạnh được gắn nhãn với trọng số của nó, ở đây tương đương với chiều dài của nó.

![Minimum Spanning Tree](https://upload.wikimedia.org/wikipedia/commons/c/c9/Multiple_minimum_spanning_trees.svg)

Hình này cho thấy có thể có nhiều hơn một cây khung nhỏ nhất trong một đồ thị. Trong hình, hai cây dưới đồ thị là hai khả năng của cây khung nhỏ nhất của đồ thị đã cho.

## Tài liệu tham khảo

- [Cây Khung Nhỏ Nhất trên Wikipedia](https://en.wikipedia.org/wiki/Minimum_spanning_tree)
- [Thuật toán Kruskal trên Wikipedia](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm)
- [Thuật toán Kruskal trên YouTube bởi Tushar Roy](https://www.youtube.com/watch?v=fAuF0EuZVCk&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [Thuật toán Kruskal trên YouTube bởi Michael Sambol](https://www.youtube.com/watch?v=71UQH7Pr9kU&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
