# Tìm kiếm nhị phân

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, tìm kiếm nhị phân, còn được gọi là tìm kiếm nửa khoảng, tìm kiếm theo logarithmic, hoặc chia nhị phân, là một thuật toán tìm kiếm mục tiêu trong một mảng đã được sắp xếp. Tìm kiếm nhị phân so sánh giá trị mục tiêu với phần tử ở giữa của mảng; nếu chúng không bằng nhau, một nửa mà mục tiêu không thể nằm ở đó sẽ bị loại bỏ và tìm kiếm tiếp tục trên nửa còn lại cho đến khi thành công. Nếu tìm kiếm kết thúc với nửa còn lại là trống, mục tiêu không có trong mảng.

![Tìm kiếm nhị phân](https://upload.wikimedia.org/wikipedia/commons/8/83/Binary_Search_Depiction.svg)

## Phức tạp

**Phức tạp thời gian**: `O(log(n))` - vì chúng ta chia khu vực tìm kiếm thành hai cho mỗi vòng lặp tiếp theo.

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Binary_search_algorithm)
- [YouTube](https://www.youtube.com/watch?v=P3YID7liBug&index=29&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
