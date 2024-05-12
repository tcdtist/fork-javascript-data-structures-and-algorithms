# Sắp xếp theo thùng - Bucket Sort

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Bucket sort**, hoặc **bin sort**, là một thuật toán sắp xếp hoạt động bằng cách phân phối các phần tử của một mảng vào một số thùng. Sau đó, mỗi thùng được sắp xếp riêng lẻ, entweder bằng cách sử dụng một thuật toán sắp xếp khác, hoặc bằng cách áp dụng đệ quy thuật toán sắp xếp thùng.

## Thuật toán

Bucket sort hoạt động như sau:

1. Thiết lập một mảng `thùng` ban đầu là trống.
2. **Phân tán:** Duyệt qua mảng gốc, đặt mỗi đối tượng vào `thùng` của nó.
3. Sắp xếp mỗi `thùng` không trống.
4. **Tập hợp:** Ghé thăm các `thùng` theo thứ tự và đặt tất cả các phần tử lại vào mảng gốc.

Các phần tử được phân phối trong các thùng:

![Elements are distributed among bins](./images/bucket_sort_1.png)

Sau đó, các phần tử được sắp xếp trong mỗi thùng:

![Elements are sorted within each bin](./images/bucket_sort_2.png)

## Phức tạp

Độ phức tạp tính toán phụ thuộc vào thuật toán được sử dụng để sắp xếp mỗi thùng, số lượng thùng được sử dụng, và liệu đầu vào có phân phối đồng đều không.

Trong trường hợp **tệ nhất**, độ phức tạp thời gian của bucket sort là `O(n^2)` nếu thuật toán sắp xếp được sử dụng trên thùng là _sắp xếp chèn_, là trường hợp sử dụng phổ biến nhất vì kỳ vọng là các thùng sẽ không có quá nhiều phần tử so với toàn bộ danh sách. Trong trường hợp tệ nhất, tất cả các phần tử được đặt vào một thùng, làm cho thời gian chạy giảm xuống đến độ phức tạp tệ nhất của sắp xếp chèn (tất cả các phần tử đều theo thứ tự ngược lại). Nếu độ phức tạp thời gian tệ nhất của sắp xếp trung gian được sử dụng là `O(n * log(n))`, thì độ phức tạp thời gian tệ nhất của bucket sort cũng sẽ là
`O(n * log(n))`.

Trên **trung bình**, khi phân phối các phần tử qua các thùng khá đồng đều, có thể chứng minh rằng bucket sort chạy trung bình là `O(n + k)` cho `k` thùng.

## Tham khảo

- [Bucket Sort trên Wikipedia](https://en.wikipedia.org/wiki/Bucket_sort)
