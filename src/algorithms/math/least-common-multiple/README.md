# Least common multiple - Bội số chung nhỏ nhất

_Xem bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong toán học và lý thuyết số, bội số chung nhỏ nhất,
hoặc bội số chung nhỏ nhất của hai số nguyên dương `a` và `b`,
thường được ký hiệu là `LCM(a, b)`, là số nguyên dương nhỏ nhất
mà chia hết cho cả `a` và `b`. Vì phép chia của số nguyên cho không
là không xác định, định nghĩa này chỉ có ý nghĩa khi `a` và `b` đều
khác không. Tuy nhiên, một số tác giả định nghĩa `lcm(a,0)`
là `0` cho tất cả các `a`, điều này là kết quả của việc lấy
`lcm` là giá trị nhỏ nhất trong lưới của tính chia hết.

## Ví dụ

LCM của 4 và 6 là gì?

Các bội số của `4` là:

```
4, 8, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48, 52, 56, 60, 64, 68, 72, 76, ...
```

và các bội số của `6` là:

```
6, 12, 18, 24, 30, 36, 42, 48, 54, 60, 66, 72, ...
```

Các bội số chung của `4` và `6` đơn giản là các số
nằm trong cả hai danh sách:

```
12, 24, 36, 48, 60, 72, ....
```

Vậy, từ danh sách này của một số bội số chung đầu tiên của
các số `4` và `6`, bội số chung nhỏ nhất của chúng là `12`.

## Tính bội số chung nhỏ nhất

Công thức sau đây giảm bài toán tính bội số chung nhỏ nhất
xuống thành bài toán tính ước số chung lớn nhất (GCD), còn được gọi là ước số chung lớn nhất:

```
lcm(a, b) = |a * b| / gcd(a, b)
```

![LCM](https://upload.wikimedia.org/wikipedia/commons/c/c9/Symmetrical_5-set_Venn_diagram_LCM_2_3_4_5_7.svg)

Một biểu đồ Venn hiển thị các bội số chung nhỏ nhất của
các tổ hợp của `2`, `3`, `4`, `5` và `7` (`6` bị bỏ qua vì
nó là `2 × 3`, cả hai đều đã được đại diện).

Ví dụ, một trò chơi bài yêu cầu các lá bài của nó
phải được chia đều cho tối đa `5` người chơi yêu cầu ít nhất `60`
lá bài, số tại giao của các tập hợp `2`, `3`, `4`
và `5`, nhưng không phải là tập hợp `7`.

## Tài Liệu Tham Khảo

[Wikipedia](https://en.wikipedia.org/wiki/Least_common_multiple)
