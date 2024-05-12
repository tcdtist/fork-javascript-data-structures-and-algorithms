# Bài toán Đường đi duy nhất

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Một con robot đang được đặt ở góc trên cùng bên trái của một lưới `m x n`
(mô tả là 'Bắt đầu' trong hình dưới đây).

Robot chỉ có thể di chuyển xuống hoặc sang phải tại bất kỳ thời điểm nào.
Robot đang cố gắng đến góc dưới cùng bên phải của lưới (được đánh dấu là 'Kết thúc'
trong hình dưới đây).

Có bao nhiêu đường đi duy nhất có thể có?

![Đường đi duy nhất](https://leetcode.com/static/images/problemset/robot_maze.png)

## Ví dụ

**Ví dụ #1**

```
Đầu vào: m = 3, n = 2
Đầu ra: 3
Giải thích:
Từ góc trên cùng bên trái, có tổng cộng 3 cách để đến góc dưới cùng bên phải:
1. Sang phải -> Sang phải -> Xuống
2. Sang phải -> Xuống -> Sang phải
3. Xuống -> Sang phải -> Sang phải
```

**Ví dụ #2**

```
Đầu vào: m = 7, n = 3
Đầu ra: 28
```

## Thuật toán

### Quay lui

Ý tưởng đầu tiên mà có thể nghĩ đến là chúng ta cần xây dựng một cây quyết định
trong đó `D` có nghĩa là di chuyển xuống và `R` có nghĩa là di chuyển sang phải.
Ví dụ trong trường hợp bảng `chiều rộng = 3` và `chiều cao = 2` chúng ta sẽ có cây
quyết định như sau:

```
                BẮT ĐẦU
                /   \
               D     R
             /     /   \
           R      D      R
         /      /         \
        R      R            D

       KẾT THÚC KẾT THÚC KẾT THÚC
```

Chúng ta có thể thấy ba nhánh duy nhất ở đây đó là câu trả lời cho vấn đề của chúng ta.

**Độ phức tạp thời gian**: `O(2 ^ n)` - khoảng cách xấp xỉ trong trường hợp xấu nhất
với bảng vuông có kích thước `n`.

**Độ phức tạp không gian phụ**: `O(m + n)` - vì chúng ta cần lưu trữ đường đi hiện tại với
các vị trí.

### Lập trình động

Hãy xem `BẢNG[i][j]` như là bài toán phụ của chúng ta.

Khi chúng ta có hạn chế chỉ được di chuyển sang phải
và xuống, chúng ta có thể nói rằng số lượng đường đi duy nhất đến ô hiện
tại là tổng của số lượng đường đi duy nhất đến ô phía trên ô hiện tại
và ô bên trái của ô hiện tại.

```
BẢNG[i][j] = BẢNG[i - 1][j] + BẢNG[i][j - 1]; // vì chúng ta chỉ có thể di chuyển xuống hoặc sang phải.
```

Các trường hợp cơ sở là:

```
BẢNG[0][bất kỳ] = 1; // chỉ có một cách để đến bất kỳ ô trên cùng nào.
BẢNG[bất kỳ][0] = 1; // chỉ có một cách để đến bất kỳ ô nào trong cột bên trái.
```

Đối với bảng `3 x 2` của chúng ta, ma trận lập trình động sẽ trông như sau:

|       |  0  |  1  |  1  |
| :---: | :-: | :-: | :-: |
| **0** |  0  |  1  |  1  |
| **1** |  1  |  2  |  3  |

Mỗi ô chứa số lượng đường đi duy nhất đến nó. Chúng ta cần
ô phía dưới bên phải với số `3`.

**Độ phức tạp thời gian**: `O(m * n)` - vì chúng ta đi qua mỗi ô của ma trận lập trình động.

**Độ phức tạp không gian phụ**: `O(m * n)` - vì chúng ta cần có ma trận lập trình động.

### Dựa trên Tam giác Pascal

Câu hỏi này thực sự là một dạng khác của Tam giác Pascal.

Góc của hình chữ nhật này ở dòng `m + n - 2`, và
ở vị trí `min(m, n) - 1` của Tam giác Pascal.

## Tham khảo

- [LeetCode](https://leetcode.com/problems/unique-paths/description/)
