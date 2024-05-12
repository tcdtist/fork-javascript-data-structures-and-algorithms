# Thuật toán k-Means

**Thuật toán k-Means** là một thuật toán Học máy không giám sát. Đây là một thuật toán phân cụm, nhóm dữ liệu mẫu dựa trên sự tương đồng giữa các chiều của các vector.

Trong phân loại k-Means, đầu ra là một tập hợp các lớp được gán cho mỗi vector. Vị trí của mỗi cụm được tối ưu liên tục để có được các vị trí chính xác của mỗi cụm sao cho chúng đại diện cho mỗi nhóm một cách rõ ràng.

Ý tưởng là tính toán sự tương đồng giữa vị trí của cụm và các vector dữ liệu, và gán lại các cụm dựa trên điều đó. [Khoảng cách Euclid](https://github.com/trekhleb/javascript-algorithms/tree/master/src/algorithms/math/euclidean-distance) thường được sử dụng cho nhiệm vụ này.

![Khoảng cách Euclid giữa hai điểm](https://upload.wikimedia.org/wikipedia/commons/5/55/Euclidean_distance_2d.svg)

_Nguồn ảnh: [Wikipedia](https://en.wikipedia.org/wiki/Euclidean_distance)_

Thuật toán được thực hiện như sau:

1. Kiểm tra lỗi như dữ liệu không hợp lệ/không nhất quán
2. Khởi tạo vị trí của `k` cụm với `k` điểm ban đầu/ngẫu nhiên
3. Tính khoảng cách từ mỗi điểm dữ liệu đến mỗi cụm
4. Gán nhãn cụm của mỗi điểm dữ liệu bằng nhãn của cụm ở khoảng cách tối thiểu của nó
5. Tính trọng tâm của mỗi cụm dựa trên các điểm dữ liệu mà nó chứa
6. Lặp lại từng bước trên cho đến khi vị trí trọng tâm thay đổi

Dưới đây là một hình dung về phân cụm k-Means để hiểu rõ hơn:

![Trực quan hóa k-Means](https://upload.wikimedia.org/wikipedia/commons/e/ea/K-means_convergence.gif)

_Nguồn ảnh: [Wikipedia](https://en.wikipedia.org/wiki/K-means_clustering)_

Trọng tâm di chuyển liên tục để tạo ra sự phân biệt tốt hơn giữa các tập hợp dữ liệu khác nhau. Như chúng ta có thể thấy, sau một số lần lặp, sự khác biệt về trọng tâm khá thấp giữa các lần lặp. Ví dụ, giữa các lần lặp `13` và `14`, sự khác biệt khá nhỏ vì ở đó trình tối ưu hóa đang điều chỉnh các trường hợp ranh giới.

## Ví dụ mã

- [kMeans.js](./kMeans.js)
- [kMeans.test.js](./__test__/kMeans.test.js) (các ca kiểm thử)

## Tham khảo

- [Thuật toán k-Means trên Wikipedia](https://en.wikipedia.org/wiki/K-means_clustering)
