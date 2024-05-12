# Sắp xếp trộn - Merge Sort

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, sắp xếp trộn (thường được viết là mergesort) là một thuật toán sắp xếp hiệu quả, đa dụng, dựa trên so sánh. Hầu hết các phiên bản sản xuất một sắp xếp ổn định, có nghĩa là việc triển khai bảo tồn thứ tự đầu vào của các phần tử bằng nhau trong đầu ra đã sắp xếp. Mergesort là một thuật toán chia để trị được phát minh bởi John von Neumann vào năm 1945.

Một ví dụ về sắp xếp trộn. Đầu tiên chia danh sách thành đơn vị nhỏ nhất (1 phần tử), sau đó so sánh mỗi phần tử với danh sách liền kề để sắp xếp và trộn hai danh sách liền kề. Cuối cùng tất cả các phần tử được sắp xếp và trộn lại.

![Sắp xếp Trộn](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

Một thuật toán sắp xếp trộn đệ quy được sử dụng để sắp xếp một mảng gồm 7 giá trị số nguyên. Đây là các bước mà một con người sẽ thực hiện để mô phỏng sắp xếp trộn (từ trên xuống).

![Sắp xếp Trộn](https://upload.wikimedia.org/wikipedia/commons/e/e6/Merge_sort_algorithm_diagram.svg)

## Phức tạp

| Tên              |   Tốt nhất    |  Trung bình   |    Tệ nhất    | Bộ nhớ | Ổn định | Bình luận |
| ---------------- | :-----------: | :-----------: | :-----------: | :----: | :-----: | :-------- |
| **Sắp xếp trộn** | n&nbsp;log(n) | n&nbsp;log(n) | n&nbsp;log(n) |   n    |   Có    |           |

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Merge_sort)
- [YouTube](https://www.youtube.com/watch?v=KF2j-9iSf4Q&index=27&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
