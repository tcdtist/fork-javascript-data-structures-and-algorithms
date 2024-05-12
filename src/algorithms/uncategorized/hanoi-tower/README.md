# Tháp Hà Nội

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Tháp Hà Nội (cũng được gọi là Tháp Brahma hoặc Tháp Lucas và đôi khi được sử dụng số ít) là một trò chơi hoặc bài toán toán học.
Nó bao gồm ba thanh và một số đĩa có kích thước khác nhau,
có thể trượt lên bất kỳ thanh nào. Bài toán bắt đầu với các đĩa được xếp gọn theo thứ tự tăng dần về kích thước trên một thanh, với đĩa nhỏ nhất ở trên cùng, tạo thành một hình nón.

Mục tiêu của bài toán là di chuyển toàn bộ các đĩa sang một thanh khác,
tuân theo các quy tắc đơn giản sau đây:

- Chỉ có thể di chuyển một đĩa mỗi lần.
- Mỗi lần di chuyển bao gồm việc lấy đĩa trên cùng từ một trong các thanh và đặt nó lên trên đỉnh của một thanh khác hoặc trên một thanh trống.
- Không có đĩa nào được đặt lên trên đĩa nhỏ hơn.

![Tháp Hà Nội](https://upload.wikimedia.org/wikipedia/commons/8/8d/Iterative_algorithm_solving_a_6_disks_Tower_of_Hanoi.gif)

Phim hoạt hình của một thuật toán lặp giải quyết bài toán với 6 đĩa

Với `3` đĩa, bài toán có thể giải quyết trong `7` bước. Số lần di chuyển tối thiểu cần thiết để giải quyết bài toán Tháp Hà Nội
là `2^n - 1`, trong đó `n` là số đĩa.

## Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Tower_of_Hanoi)
- [HackerEarth](https://www.hackerearth.com/blog/algorithms/tower-hanoi-recursion-game-algorithm-explained/)
