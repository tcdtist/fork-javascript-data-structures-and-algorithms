# Bảng Băm

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong lĩnh vực máy tính, **bảng băm** (hash map) là một cấu trúc dữ liệu mà triển khai một loại dữ liệu trừu tượng gọi là _mảng kết hợp_, một cấu trúc có thể _ánh xạ các khóa sang các giá trị_. Một bảng băm sử dụng một _hàm băm_ để tính toán một chỉ số vào một mảng các ô hoặc khe, từ đó giá trị mong muốn có thể được tìm thấy.

Lý tưởng, hàm băm sẽ gán mỗi khóa vào một khe duy nhất, nhưng hầu hết các thiết kế bảng băm sử dụng một hàm băm không hoàn hảo, có thể gây ra _xung đột băm_ khi hàm băm tạo ra cùng một chỉ số cho nhiều hơn một khóa. Những xung đột như vậy phải được xử lý một cách nào đó.

![Bảng Băm](./images/hash-table.jpeg)

Xung đột băm được giải quyết bằng phương pháp chuỗi riêng.

![Xung Đột Băm](./images/collision-resolution.jpeg)

_Tạo với [okso.app](https://okso.app)_

## Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Hash_table)
- [YouTube](https://www.youtube.com/watch?v=shs0KM3wKv8&index=4&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
