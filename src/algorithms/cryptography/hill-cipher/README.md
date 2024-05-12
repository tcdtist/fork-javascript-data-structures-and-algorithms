# Thuật toán Mật mã Hill

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Mật mã Hill là một loại [mật mã thay thế đa ký tự](https://en.wikipedia.org/wiki/Polygraphic_substitution) dựa trên đại số tuyến tính.

Mỗi chữ cái được biểu diễn bằng một số [theo modulo](https://en.wikipedia.org/wiki/Modular_arithmetic) `26`. Mặc dù đây không phải là tính năng thiết yếu của thuật toán, nhưng đây là một phương án đơn giản thường được sử dụng:

| **Chữ cái** | A   | B   | C   | D   | E   | F   | G   | H   | I   | J   | K   | L   | M   | N   | O   | P   | Q   | R   | S   | T   | U   | V   | W   | X   | Y   | Z   |
| ----------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Số**      | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  | 12  | 13  | 14  | 15  | 16  | 17  | 18  | 19  | 20  | 21  | 22  | 23  | 24  | 25  |

## Mã hóa

Để mã hóa một thông điệp, mỗi khối `n` chữ cái (xem như một vector `n` thành phần) được nhân với một ma trận `n × n` khả nghịch, với modulo `26`.

Ma trận được sử dụng để mã hóa là _khóa mật mã_, và nó nên được chọn ngẫu nhiên từ tập hợp các ma trận `n × n` khả nghịch (theo modulo `26`). Mật mã có thể được điều chỉnh cho bảng chữ cái với bất kỳ số lượng chữ cái nào; tất cả các phép tính chỉ cần được thực hiện theo modulo số lượng chữ cái thay vì modulo `26`.

Xét thông điệp `ACT`, và khóa dưới đây (hoặc `GYB/NQK/URP` bằng chữ):

```
| 6   24   1  |
| 13  16   10 |
| 20  17   15 |
```

Vì `A` là `0`, `C` là `2` và `T` là `19`, thông điệp là vector:

```
|  0  |
|  2  |
|  19 |
```

Do đó, vector được mã hóa là:

```
| 6   24   1  |  |  0  |   |  67  |   |  15 |
| 13  16   10 |  |  2  | = |  222 | ≡ |  14 | (mod 26)
| 20  17   15 |  |  19 |   |  319 |   |  7  |
```

tương ứng với văn bản mã hóa là `POH`.

Bây giờ, giả sử rằng thông điệp của chúng ta là `CAT` (lưu ý là chúng ta đang sử dụng cùng các chữ cái như trong `ACT` ở đây), hoặc:

```
|  2  |
|  0  |
|  19 |
```

Lần này, vector được mã hóa là:

```
| 6   24   1  |  |  2  |   |  31  |   |  5  |
| 13  16   10 |  |  0  | = |  216 | ≡ |  8  | (mod 26)
| 20  17   15 |  |  19 |   |  325 |   |  13 |
```

tương ứng với văn bản mã hóa là `FIN`. Mỗi chữ cái đã thay đổi.

## Giải mã

Để giải mã thông điệp, mỗi khối được nhân với nghịch đảo của ma trận được sử dụng để mã hóa. Chúng ta chuyển văn bản mã hóa trở lại thành vector, sau đó chỉ đơn giản nhân với ma trận nghịch đảo của ma trận khóa (`IFK/VIV/VMI` bằng chữ). (Xem [nghịch đảo ma trận](https://en.wikipedia.org/wiki/Matrix_inversion) để biết các phương pháp tính ma trận nghịch đảo.) Chúng ta thấy rằng, theo modulo 26, ma trận nghịch đảo của ma trận được sử dụng trong ví dụ trước là:

```
                -1
| 6   24   1  |                | 8   5    10 |
| 13  16   10 |    (mod 26) ≡  | 21  8    21 |
| 20  17   15 |                | 21  12   8  |
```

Lấy ví dụ văn bản mã hóa trước là `POH`, chúng ta có:

```
| 8   5    10 |  |  15 |   |  260 |   |  0  |
| 21  8    21 |  |  14 | = |  574 | ≡ |  2  | (mod 26)
| 21  12   8  |  |  7  |   |  539 |   |  19 |
```

đưa chúng ta trở lại `ACT`, như mong đợi.

## Định nghĩa ma trận mã hóa

Có hai vấn đề tồn tại trong việc chọn ma trận mã hóa:

1. Không phải tất cả các ma trận đều có nghịch đảo. Ma trận sẽ có nghịch đảo nếu và chỉ nếu [định thức](https://en.wikipedia.org/wiki/Determinant) của nó không phải là không.
2. Định thức của ma trận mã hóa không được có các yếu tố chung với cơ số modulo.

Do đó, nếu chúng ta làm việc theo modulo `26` như trên, định thức phải khác không và không được chia hết cho `2` hoặc `13`. Nếu định thức là `0` hoặc có các yếu tố chung với cơ sở modulo, thì ma trận đó không thể được sử dụng trong mật mã Hill, và một ma trận khác phải được chọn (nếu không sẽ không thể giải mã). May mắn thay, các ma trận đáp ứng điều kiện để sử dụng trong mật mã Hill khá phổ biến.

## Tài liệu tham khảo

- [Mật mã Hill trên Wikipedia](https://en.wikipedia.org/wiki/Hill_cipher)
- [Nghịch đảo ma trận trên MathIsFun](https://www.mathsisfun.com/algebra/matrix-inverse.html)
- [GeeksForGeeks](https://www.geeksforgeeks.org/hill-cipher/)
