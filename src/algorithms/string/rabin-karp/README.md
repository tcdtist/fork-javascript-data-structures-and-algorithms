# Thuật toán Rabin-Karp

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, thuật toán Rabin–Karp hoặc thuật toán Karp–Rabin là một thuật toán tìm kiếm chuỗi được tạo ra bởi Richard M. Karp và Michael O. Rabin (năm 1987) sử dụng hàm băm để tìm bất kỳ một trong một tập hợp các chuỗi mẫu trong một văn bản.

## Thuật toán

Thuật toán Rabin–Karp cố gắng tăng tốc quá trình kiểm tra sự bằng nhau của mẫu với các chuỗi con trong văn bản bằng cách sử dụng một hàm băm. Một hàm băm là một hàm chuyển đổi mỗi chuỗi thành một giá trị số, gọi là giá trị băm của nó; ví dụ, chúng ta có thể có `hash('hello') = 5`. Thuật toán tận dụng việc nếu hai chuỗi bằng nhau, thì giá trị băm của chúng cũng bằng nhau. Do đó, việc khớp chuỗi được giảm bớt (gần như) thành việc tính giá trị băm của mẫu tìm kiếm và sau đó tìm chuỗi con của chuỗi đầu vào với giá trị băm đó.

Tuy nhiên, có hai vấn đề với phương pháp này. Đầu tiên, vì có rất nhiều chuỗi khác nhau và rất ít giá trị băm, một số chuỗi khác biệt sẽ có cùng một giá trị băm. Nếu các giá trị băm khớp nhau, mẫu và chuỗi con có thể không khớp; do đó, sự khớp của tiềm năng của mẫu tìm kiếm và chuỗi con phải được xác nhận bằng cách so sánh chúng; việc so sánh đó có thể mất thời gian đối với các chuỗi con dài. May mắn thay, một hàm băm tốt trên các chuỗi hợp lý thường không có nhiều va chạm, vì vậy thời gian tìm kiếm kỳ vọng sẽ được chấp nhận.

## Hàm Băm Sử Dụng

Chìa khóa của hiệu suất của thuật toán Rabin–Karp là tính toán hiệu quả giá trị băm của các chuỗi con kế tiếp của văn bản. **Dấu vân tay Rabin** là một hàm băm trượt phổ biến và hiệu quả.

**Hàm băm đa thức** mô tả trong ví dụ này không phải là một dấu vân tay Rabin, nhưng nó hoạt động cũng tốt. Nó xem mọi chuỗi con như một số trong một cơ số nào đó, cơ sở thường là một số nguyên tố lớn.

## Phức Tạp

Đối với văn bản có độ dài `n` và `p` mẫu với tổng độ dài `m`, thời gian chạy trung bình và tốt nhất là `O(n + m)` trong không gian `O(p)`, nhưng thời gian xấu nhất là `O(n * m)`.

## Ứng Dụng

Một ứng dụng thực tế của thuật toán là phát hiện sự sao chép. Dựa trên nguồn, thuật toán có thể tìm kiếm nhanh chóng qua một bài báo để tìm các câu từ nguồn, bỏ qua các chi tiết như chữ hoa và dấu câu. Vì sự phong phú của các chuỗi cần tìm, các thuật toán tìm kiếm chuỗi đơn lẻ không thực tế.

## Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Rabin%E2%80%93Karp_algorithm)
- [YouTube](https://www.youtube.com/watch?v=H4VrKHVG5qI&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
