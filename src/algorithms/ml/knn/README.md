# Thuật toán k-Nearest Neighbors (k-NN)

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Thuật toán k-Nearest Neighbors (k-NN)** là một thuật toán Học máy có giám sát. Đây là một thuật toán phân loại, xác định lớp của một vector mẫu bằng cách sử dụng dữ liệu mẫu.

Trong phân loại k-NN, đầu ra là một lớp. Một đối tượng được phân loại bằng cách bầu chọn đa số của các láng giềng của nó, với đối tượng được gán cho lớp phổ biến nhất trong `k` láng giềng gần nhất của nó (`k` là một số nguyên dương, thường nhỏ). Nếu `k = 1`, thì đối tượng được gán đơn giản cho lớp của láng giềng gần nhất duy nhất đó.

Ý tưởng là tính toán sự tương đồng giữa hai điểm dữ liệu dựa trên một phép đo khoảng cách. [Khoảng cách Euclid](https://en.wikipedia.org/wiki/Euclidean_distance) thường được sử dụng cho nhiệm vụ này.

![Khoảng cách Euclid giữa hai điểm](https://upload.wikimedia.org/wikipedia/commons/5/55/Euclidean_distance_2d.svg)

_Nguồn ảnh: [Wikipedia](https://en.wikipedia.org/wiki/Euclidean_distance)_

Thuật toán được thực hiện như sau:

1. Kiểm tra lỗi như dữ liệu/nhãn không hợp lệ.
2. Tính khoảng cách Euclid của tất cả các điểm dữ liệu trong dữ liệu huấn luyện với điểm phân loại
3. Sắp xếp các khoảng cách của các điểm cùng với lớp của chúng theo thứ tự tăng dần
4. Lấy `K` lớp ban đầu và tìm chế độ để có được lớp giống nhất nhất
5. Báo cáo lớp giống nhất

Dưới đây là một hình dung về phân loại k-NN để hiểu rõ hơn:

![Trực quan hóa k-NN](https://upload.wikimedia.org/wikipedia/commons/e/e7/KnnClassification.svg)

_Nguồn ảnh: [Wikipedia](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)_

Mẫu kiểm tra (chấm xanh lá cây) sẽ được phân loại vào các hình vuông màu xanh lá cây hoặc các tam giác màu đỏ. Nếu `k = 3` (vòng tròn đường kín) nó được gán cho các tam giác màu đỏ vì có `2` tam giác và chỉ có `1` hình vuông trong vòng tròn trong. Nếu `k = 5` (vòng tròn đường kẻ đứt) nó được gán cho các hình vuông màu xanh (`3` hình vuông so với `2` tam giác trong vòng tròn bên ngoài).

Một ví dụ khác về phân loại k-NN:

![Trực quan hóa k-NN](https://media.geeksforgeeks.org/wp-content/uploads/graph2-2.png)

_Nguồn ảnh: [GeeksForGeeks](https://media.geeksforgeeks.org/wp-content/uploads/graph2-2.png)_

Ở đây, như chúng ta có thể thấy, việc phân loại các điểm không xác định sẽ được đánh giá bằng sự gần gũi của chúng đối với các điểm khác.

Lưu ý rằng `K` được ưa chuộng là có các giá trị lẻ để phá vỡ sự ràng buộc. Thông thường `K` được lấy là `3` hoặc `5`.

## Tham khảo

- [Thuật toán k-nearest neighbors trên Wikipedia](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)
