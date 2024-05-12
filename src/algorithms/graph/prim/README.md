# Thuật toán Prim - Prim's Algorithm

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

Trong khoa học máy tính, **Thuật toán Prim** là một thuật toán tham lam tìm cây khung nhỏ nhất cho một đồ thị vô hướng có trọng số.

Thuật toán hoạt động bằng cách xây dựng cây này từng đỉnh một lần, bắt đầu từ một đỉnh bất kỳ, và tại mỗi bước thêm vào kết nối có chi phí thấp nhất có thể từ cây tới một đỉnh khác.

![Prim's Algorithm](https://upload.wikimedia.org/wikipedia/commons/f/f7/Prim%27s_algorithm.svg)

Thuật toán Prim bắt đầu tại đỉnh `A`. Ở bước thứ ba, cạnh `BD` và `AB` đều có trọng số `2`, do đó `BD` được chọn một cách ngẫu nhiên. Sau bước đó, `AB` không còn là ứng viên để được thêm vào cây vì nó nối hai nút đã có trong cây.

## Cây Khung Nhỏ Nhất - Minimum Spanning Tree

Một **cây khung nhỏ nhất** (MST) hay cây khung có trọng số nhỏ nhất là một tập hợp các cạnh của một đồ thị liên thông, có trọng số cạnh, (không) có hướng nối tất cả các đỉnh lại với nhau, không có chu trình và có tổng trọng số cạnh nhỏ nhất có thể. Nói cách khác, đó là một cây khung mà tổng trọng số của các cạnh là nhỏ nhất có thể. Một cách tổng quát hơn, bất kỳ đồ thị có trọng số cạnh không có hướng (không nhất thiết phải liên thông) đều có một rừng khung nhỏ nhất, là sự kết hợp của các cây khung nhỏ nhất cho các thành phần liên thông của nó.

![Minimum Spanning Tree](https://upload.wikimedia.org/wikipedia/commons/d/d2/Minimum_spanning_tree.svg)

Một đồ thị phẳng và cây khung nhỏ nhất của nó. Mỗi cạnh được gắn nhãn với trọng số của nó, ở đây tương đương với chiều dài của nó.

![Minimum Spanning Tree](https://upload.wikimedia.org/wikipedia/commons/c/c9/Multiple_minimum_spanning_trees.svg)

Hình này cho thấy có thể có nhiều hơn một cây khung nhỏ nhất trong một đồ thị. Trong hình, hai cây dưới đồ thị là hai khả năng của cây khung nhỏ nhất của đồ thị đã cho.

## Tài liệu tham khảo

- [Cây Khung Nhỏ Nhất trên Wikipedia](https://en.wikipedia.org/wiki/Minimum_spanning_tree)
- [Thuật toán Prim trên Wikipedia](https://en.wikipedia.org/wiki/Prim%27s_algorithm)
- [Thuật toán Prim trên YouTube bởi Tushar Roy](https://www.youtube.com/watch?v=oP2-8ysT3QQ&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [Thuật toán Prim trên YouTube bởi Michael Sambol](https://www.youtube.com/watch?v=cplfcGZmX7I&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
