# Thuật toán Knuth–Morris–Pratt

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Thuật toán tìm kiếm chuỗi Knuth–Morris–Pratt (hoặc thuật toán KMP) tìm kiếm các lần xuất hiện của một "từ" `W` trong một "chuỗi văn bản chính" `T` bằng cách sử dụng quan sát rằng khi một không khớp xảy ra, từ chính nó cung cấp đủ thông tin để xác định nơi mà sự khớp tiếp theo có thể bắt đầu, qua đó bỏ qua việc kiểm tra lại các ký tự đã khớp trước đó.

## Độ phức tạp

- **Thời gian:** `O(|W| + |T|)` (nhanh hơn nhiều so với phương pháp trực tiếp `O(|W| * |T|)`)
- **Không gian:** `O(|W|)`

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)
- [YouTube](https://www.youtube.com/watch?v=GTJr8OvyEVQ&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
