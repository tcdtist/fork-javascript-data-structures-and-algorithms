# Xoay ma trận vuông tại chỗ

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

## Vấn đề

Bạn được cho một ma trận 2D `n x n` (đại diện cho một hình ảnh).
Xoay ma trận theo góc `90` độ (theo chiều kim đồng hồ).

**Lưu Ý**

Bạn phải xoay hình ảnh **tại chỗ**, điều này có nghĩa là bạn
phải sửa đổi trực tiếp ma trận 2D đầu vào. **KHÔNG** phải cấp
phát một ma trận 2D khác và thực hiện xoay.

## Ví dụ

**Ví dụ #1**

Ma trận đầu vào được cho:

```
[
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
]
```

Xoay ma trận đầu vào tại chỗ sao cho nó trở thành:

```
[
  [7, 4, 1],
  [8, 5, 2],
  [9, 6, 3],
]
```

**Ví dụ #2**

Ma trận đầu vào được cho:

```
[
  [5, 1, 9, 11],
  [2, 4, 8, 10],
  [13, 3, 6, 7],
  [15, 14, 12, 16],
]
```

Xoay ma trận đầu vào tại chỗ sao cho nó trở thành:

```
[
  [15, 13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7, 10, 11],
]
```

## Thuật Toán

Chúng ta cần thực hiện hai phản chiếu của ma trận:

- phản chiếu theo chiều dọc
- phản chiếu theo đường chéo từ dưới lên trên từ góc dưới bên trái đến góc trên bên phải

Hoặc bạn cũng có thể phản chiếu theo đường chéo từ trên xuống dưới và phản chiếu theo chiều ngang.

Một câu hỏi phổ biến là làm sao bạn có thể tìm ra loại phản chiếu nào để thực hiện? Đơn giản là lấy một tờ giấy vuông, viết một từ ngẫu nhiên trên đó để bạn biết nó đã được xoay. Sau đó, quay tờ giấy vuông cho đến khi bạn tìm ra cách để đến được giải pháp.

Dưới đây là một ví dụ về cách dòng đầu tiên có thể được xoay bằng cách sử dụng phản chiếu đường chéo từ trên xuống dưới và phản chiếu theo chiều ngang.

```
Hãy nói chúng ta có một chuỗi ở đầu của ma trận:

A B C
• • •
• • •

Hãy thực hiện phản chiếu đường chéo từ trên xuống dưới:

A B C
/ / •
/ • •

Và bây giờ hãy thực hiện phản chiếu theo chiều ngang:

A → →
B → →
C → →

Chuỗi đã được xoay 90 độ:

• • A
• • B
• • C
```

## Tham Khảo

- [LeetCode](https://leetcode.com/problems/rotate-image/description/)
