# Disjoint Set - Cấu Trúc Dữ Liệu Tách Biệt

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Disjoint-set** (cũng được gọi là cấu trúc dữ liệu hợp nhất-tìm hoặc cấu trúc dữ liệu hợp nhất-tìm-ghép) là một cấu trúc dữ liệu theo dõi một tập hợp các phần tử được phân chia thành một số tập hợp tách biệt (không giao nhau). Nó cung cấp các hoạt động gần như độ phức tạp hằng số (bị chặn bởi hàm Ackermann nghịch đảo) để _thêm các tập hợp mới_, _gộp các tập hợp hiện có_, và _xác định xem các phần tử có trong cùng một tập hợp không_.
Ngoài việc được sử dụng trong nhiều mục đích khác nhau (xem phần Ứng dụng), các tập hợp không giao nhau còn đóng vai trò quan trọng trong thuật toán Kruskal để tìm cây khung tối thiểu của một đồ thị.

![disjoint set](https://upload.wikimedia.org/wikipedia/commons/6/67/Dsu_disjoint_sets_init.svg)

_MakeSet_ tạo ra 8 tập hợp đơn lẻ.

![disjoint set](https://upload.wikimedia.org/wikipedia/commons/a/ac/Dsu_disjoint_sets_final.svg)

Sau một số hoạt động _Union_, một số tập hợp được nhóm lại.

## Thực hiện

- [DisjointSet.js](./DisjointSet.js)
- [DisjointSetAdhoc.js](./DisjointSetAdhoc.js) - Phiên bản tối thiểu (tạm thời) của cấu trúc dữ liệu DisjointSet (hoặc UnionFind) không có các phụ thuộc bên ngoài và dễ dàng sao chép-và-dán và sử dụng trong cuộc phỏng vấn lập trình nếu được phép bởi người phỏng vấn (vì nhiều cấu trúc dữ liệu trong JS thiếu).

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Disjoint-set_data_structure)
- [By Abdul Bari on YouTube](https://www.youtube.com/watch?v=wU6udHRIkcc&index=14&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
