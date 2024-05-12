# Sắp xếp Shell

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Sắp xếp Shell, còn được biết đến như Shell sort hoặc phương pháp Shell,
là một thuật toán so sánh in-place. Nó có thể được xem như là một
sự tổng quát hóa của sắp xếp bằng trao đổi (sắp xếp nổi bọt) hoặc sắp xếp
bằng chèn (sắp xếp chèn). Phương pháp bắt đầu bằng cách sắp xếp
các cặp phần tử cách xa nhau, sau đó dần dần
giảm khoảng cách giữa các phần tử cần so sánh. Bắt đầu
với các phần tử cách xa nhau, nó có thể di chuyển một số phần tử
nằm ngoài vị trí của chúng vào vị trí nhanh hơn so với việc trao đổi hàng xóm đơn giản.

![Sắp xếp Shell](https://upload.wikimedia.org/wikipedia/commons/d/d8/Sorting_shellsort_anim.gif)

## Cách Sắp Xếp Shell Hoạt Động

Đối với ví dụ của chúng tôi và sự dễ hiểu, chúng tôi lấy khoảng
cách là `4`. Tạo một danh sách con ảo của tất cả các giá trị nằm ở
khoảng cách 4 vị trí. Ở đây các giá trị này là
`{35, 14}`, `{33, 19}`, `{42, 27}` và `{10, 44}`

![Sắp xếp Shell](https://www.tutorialspoint.com/data_structures_algorithms/images/shell_sort_gap_4.jpg)

Chúng tôi so sánh các giá trị trong mỗi danh sách con và trao đổi chúng (nếu cần)
trong mảng ban đầu. Sau bước này, mảng mới nên
nhìn như sau

![Sắp xếp Shell](https://www.tutorialspoint.com/data_structures_algorithms/images/shell_sort_step_1.jpg)

Sau đó, chúng tôi lấy khoảng cách là 2 và khoảng cách này tạo ra hai danh sách con

- `{14, 27, 35, 42}`, `{19, 10, 33, 44}`

![Sắp xếp Shell](https://www.tutorialspoint.com/data_structures_algorithms/images/shell_sort_gap_2.jpg)

Chúng tôi so sánh và trao đổi các giá trị, nếu cần, trong mảng ban đầu.
Sau bước này, mảng nên nhìn như sau

![Sắp xếp Shell](https://www.tutorialspoint.com/data_structures_algorithms/images/shell_sort_step_2.jpg)

> Cập nhật: Trên hình ảnh dưới đây có một lỗi đánh máy và mảng kết quả cần phải là `[14, 10, 27, 19, 35, 33, 42, 44]`.

Cuối cùng, chúng tôi sắp xếp phần còn lại của mảng sử dụng khoảng cách có giá trị 1.
Sắp xếp Shell sử dụng sắp xếp chèn để sắp xếp mảng.

![Sắp xếp Shell](https://www.tutorialspoint.com/data_structures_algorithms/images/shell_sort.jpg)

## Phức Tạp

| Tên               |   Tốt nhất    |           Trung bình            |           Tệ nhất           | Bộ nhớ | Ổn định | Bình luận |
| ----------------- | :-----------: | :-----------------------------: | :-------------------------: | :----: | :-----: | :-------- |
| **Sắp xếp Shell** | n&nbsp;log(n) | phụ thuộc vào chuỗi khoảng cách | n&nbsp;(log(n))<sup>2</sup> |   1    |  Không  |           |

## Tham Khảo

- [Tutorials Point](https://www.tutorialspoint.com/data_structures_algorithms/shell_sort_algorithm.htm)
- [Wikipedia](https://en.wikipedia.org/wiki/Shellsort)
- [YouTube bởi Rob Edwards](https://www.youtube.com/watch?v=ddeLSDsYVp8&index=79&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
