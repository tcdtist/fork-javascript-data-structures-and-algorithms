# Sắp xếp Heap - Heap Sort

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Heap Sort là một thuật toán sắp xếp dựa trên so sánh. Heap Sort có thể được coi như một cải tiến của thuật toán sắp xếp chọn: giống như thuật toán đó, nó chia đầu vào của mình thành một khu vực đã sắp xếp và một khu vực chưa sắp xếp, và nó lặp lại việc thu nhỏ khu vực chưa sắp xếp bằng cách trích xuất phần tử lớn nhất và di chuyển nó vào khu vực đã sắp xếp. Sự cải tiến này bao gồm việc sử dụng cấu trúc dữ liệu heap thay vì tìm kiếm thời gian tuyến tính để tìm phần tử lớn nhất.

![Hiển thị thuật toán](https://upload.wikimedia.org/wikipedia/commons/1/1b/Sorting_heapsort_anim.gif)

![Hiển thị thuật toán](https://upload.wikimedia.org/wikipedia/commons/4/4d/Heapsort-example.gif)

## Phức tạp

| Tên           |   Tốt nhất    |  Trung bình   |    Tệ nhất    | Bộ nhớ | Ổn định | Bình luận |
| ------------- | :-----------: | :-----------: | :-----------: | :----: | :-----: | :-------- |
| **Heap sort** | n&nbsp;log(n) | n&nbsp;log(n) | n&nbsp;log(n) |   1    |  Không  |           |

## Tham khảo

[Wikipedia](https://en.wikipedia.org/wiki/Heapsort)
