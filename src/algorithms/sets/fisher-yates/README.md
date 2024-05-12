# Fisher–Yates shuffle - Trộn Fisher–Yates

_Đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trộn Fisher–Yates là một thuật toán để tạo ra một hoán vị ngẫu nhiên của một chuỗi hữu hạn—nói một cách đơn giản, thuật toán này trộn lẫn chuỗi. Thuật toán hiệu quả đặt tất cả các phần tử vào trong một cái mũ; nó liên tục xác định phần tử tiếp theo bằng cách lựa chọn một phần tử ngẫu nhiên từ cái mũ cho đến khi không còn phần tử nào còn lại. Thuật toán tạo ra một hoán vị không thiên vị: mỗi hoán vị có cùng khả năng xuất hiện. Phiên bản hiện đại của thuật toán là hiệu quả: nó tốn thời gian tỉ lệ với số lượng mục đang được trộn lẫn và trộn chúng tại chỗ.

## Tài liệu tham khảo

[Wikipedia](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle)
