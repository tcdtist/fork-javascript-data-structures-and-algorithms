# Thuật toán Floyd–Warshall

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

Trong khoa học máy tính, **thuật toán Floyd–Warshall** là một thuật toán dùng để tìm
đường đi ngắn nhất trong một đồ thị có trọng số dương hoặc âm (nhưng
không có chu trình âm). Một lần thực hiện thuật toán sẽ tìm ra
độ dài (tổng trọng số) của đường đi ngắn nhất giữa tất cả các cặp đỉnh. Mặc dù
nó không trả về chi tiết của các đường đi, nhưng có thể tái tạo
các đường đi với các thay đổi đơn giản cho thuật toán.

## Thuật toán

Thuật toán Floyd–Warshall so sánh tất cả các đường đi có thể qua đồ thị giữa
mỗi cặp đỉnh. Nó có thể làm điều này với `O(|V|^3)` so sánh trong một đồ thị.
Điều này đáng chú ý khi xét rằng có thể có tới `|V|^2` cạnh trong đồ thị,
và mọi tổ hợp cạnh đều được kiểm tra. Nó làm như vậy bằng cách cải thiện dần dần một
ước lượng về đường đi ngắn nhất giữa hai đỉnh, cho đến khi ước lượng là tối ưu.

Xem xét một đồ thị `G` với các đỉnh `V` được đánh số từ `1` đến `N`. Xem xét thêm
một hàm `shortestPath(i, j, k)` trả về đường đi ngắn nhất có thể
từ `i` đến `j` sử dụng chỉ các đỉnh từ tập `{1, 2, ..., k}` như
các điểm trung gian dọc theo đường đi. Bây giờ, với hàm này, mục tiêu của chúng ta là
tìm đường đi ngắn nhất từ mỗi `i` đến mỗi `j` sử dụng chỉ các đỉnh
trong `{1, 2, ..., N}`.

![Công thức đệ quy](https://wikimedia.org/api/rest_v1/media/math/render/svg/f9b75e25063384ccca499c56f9a279abf661ad3b)

![Công thức đệ quy](https://wikimedia.org/api/rest_v1/media/math/render/svg/34ac7c89bbb18df3fd660225fd38997079e5e513)
![Công thức đệ quy](https://wikimedia.org/api/rest_v1/media/math/render/svg/0326d6c14def89269c029da59eba012d0f2edc9d)

Công thức này là trái tim của thuật toán Floyd–Warshall.

## Ví dụ

Thuật toán trên được thực hiện trên đồ thị bên trái dưới đây:

![Ví dụ](https://upload.wikimedia.org/wikipedia/commons/2/2e/Floyd-Warshall_example.svg)

Trong các bảng dưới đây `i` là số hàng và `j` là số cột.

**k = 0**

|       |  1  |  2  |  3  |  4  |
| :---: | :-: | :-: | :-: | :-: |
| **1** |  0  |  ∞  | −2  |  ∞  |
| **2** |  4  |  0  |  3  |  ∞  |
| **3** |  ∞  |  ∞  |  0  |  2  |
| **4** |  ∞  | −1  |  ∞  |  0  |

**k = 1**

|       |  1  |  2  |  3  |  4  |
| :---: | :-: | :-: | :-: | :-: |
| **1** |  0  |  ∞  | −2  |  ∞  |
| **2** |  4  |  0  |  2  |  ∞  |
| **3** |  ∞  |  ∞  |  0  |  2  |
| **4** |  ∞  |  −  |  ∞  |  0  |

**k = 2**

|       |  1  |  2  |  3  |  4  |
| :---: | :-: | :-: | :-: | :-: |
| **1** |  0  |  ∞  | −2  |  ∞  |
| **2** |  4  |  0  |  2  |  ∞  |
| **3** |  ∞  |  ∞  |  0  |  2  |
| **4** |  3  | −1  |  1  |  0  |

**k = 3**

|       |  1  |  2  |  3  |  4  |
| :---: | :-: | :-: | :-: | :-: |
| **1** |  0  |  ∞  | −2  |  0  |
| **2** |  4  |  0  |  2  |  4  |
| **3** |  ∞  |  ∞  |  0  |  2  |
| **4** |  3  | −1  |  1  |  0  |

**k = 4**

|       |  1  |  2  |  3  |  4  |
| :---: | :-: | :-: | :-: | :-: |
| **1** |  0  | −1  | −2  |  0  |
| **2** |  4  |  0  |  2  |  4  |
| **3** |  5  |  1  |  0  |  2  |
| **4** |  3  | −1  |  1  |  0  |

## Tham khảo

- [Wikipedia](https://vi.wikipedia.org/wiki/Thu%E1%BA%ADt_to%C3%A1n_Floyd%E2%80%93Warshall)
- [YouTube (bởi Abdul Bari)](https://www.youtube.com/watch?v=oNI0rf2P9gE&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=74)
- [YouTube (bởi Tushar Roy)](https://www.youtube.com/watch?v=LwJdNfdLF9s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=75)
