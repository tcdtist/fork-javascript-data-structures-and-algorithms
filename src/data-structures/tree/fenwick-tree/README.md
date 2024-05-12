# Cây Fenwick / Cây Nhị Phân Đánh Dấu

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Cây Fenwick hoặc cây nhị phân đánh dấu là một cấu trúc dữ liệu có thể cập nhật các phần tử và tính tổng tiền tố một cách hiệu quả trong một bảng số.

So với một mảng phẳng của các số, cây Fenwick đạt được sự cân bằng tốt hơn giữa hai thao tác: cập nhật phần tử và tính tổng tiền tố. Trong một mảng phẳng của `n` số, bạn có thể lưu trữ các phần tử hoặc tổng tiền tố. Trong trường hợp đầu tiên, việc tính toán tổng tiền tố đòi hỏi thời gian tuyến tính; trong trường hợp thứ hai, việc cập nhật các phần tử mảng đòi hỏi thời gian tuyến tính (trong cả hai trường hợp, thao tác còn lại có thể được thực hiện trong thời gian hằng số). Cây Fenwick cho phép cả hai thao tác được thực hiện trong thời gian `O(log n)`. Điều này được đạt được bằng cách đại diện cho các số như một cây, trong đó giá trị của mỗi nút là tổng của các số trong cây con đó. Cấu trúc cây cho phép các thao tác được thực hiện chỉ bằng cách truy cập vào các nút `O(log n)`.

## Ghi chú về Triển khai

Cây Nhị Phân Đánh Dấu được đại diện dưới dạng một mảng. Mỗi nút của Cây Nhị Phân Đánh Dấu lưu trữ tổng của một số phần tử của mảng được cho. Kích thước của Cây Nhị Phân Đánh Dấu bằng với `n` nơi `n` là kích thước của mảng đầu vào. Trong triển khai hiện tại, chúng ta đã sử dụng kích thước là `n+1` để dễ triển khai. Tất cả các chỉ số được đánh số từ 1.

![Cây Nhị Phân Đánh Dấu](https://www.geeksforgeeks.org/wp-content/uploads/BITSum.png)

Trên hình dưới đây, bạn có thể thấy ví dụ minh họa động về việc tạo cây nhị phân đánh dấu cho mảng `[1, 2, 3, 4, 5]` bằng cách chèn từng phần tử một.

![Cây Fenwick](https://upload.wikimedia.org/wikipedia/commons/d/dc/BITDemo.gif)

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Fenwick_tree)
- [GeeksForGeeks](https://www.geeksforgeeks.org/binary-indexed-tree-or-fenwick-tree-2/)
- [YouTube](https://www.youtube.com/watch?v=CWDQJGaN1gY&index=18&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
