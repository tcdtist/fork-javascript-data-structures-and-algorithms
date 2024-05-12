# Combinations - Tổ Hợp

_Đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Khi thứ tự không quan trọng, đó là **Tổ hợp**.

Khi thứ tự **quan trọng** thì đó là **Hoán vị**.

**"Món tráng miệng của tôi là một tổ hợp của táo, nho và chuối"**
Chúng tôi không quan tâm thứ tự của các loại trái cây, chúng cũng có thể là
"chuối, nho và táo" hoặc "nho, táo và chuối",
đó là một món tráng miệng giống nhau.

## Tổ hợp không lặp lại

Đây là cách làm việc của các trò chơi xổ số. Các số được rút ra một cách
lần lượt, và nếu chúng ta có các số may mắn (bất kể thứ tự)
thì chúng ta sẽ chiến thắng!

Không Lặp Lại: chẳng hạn như các số xổ số `(2,14,15,27,30,33)`

**Số lượng tổ hợp**

![Công thức](https://www.mathsisfun.com/combinatorics/images/combinations-no-repeat.png)

trong đó `n` là số lượng thứ cần chọn từ, và chúng ta chọn `r` trong số đó,
không lặp lại, thứ tự không quan trọng.

Nó thường được gọi là "n chọn r" (như "16 chọn 3"). Và còn được gọi là Hệ số Nhị thức.

## Tổ hợp có lặp lại

Cho phép Lặp Lại: chẳng hạn như các đồng xu trong túi của bạn `(5,5,5,10,10)`

Hoặc cho rằng có năm hương vị kem:
`chuối`, `sô-cô-la`, `chanh`, `dâu` và `vanilla`.

Chúng tôi có thể chọn ba phần. Sẽ có bao nhiêu biến thể?

Hãy sử dụng các chữ cái để đại diện cho các hương vị: `{b, c, l, s, v}`.
Các lựa chọn ví dụ bao gồm:

- `{c, c, c}` (3 phần kem sô-cô-la)
- `{b, l, v}` (mỗi loại một phần của chuối, chanh và vanilla)
- `{b, v, v}` (một phần của chuối, hai phần của vanilla)

**Số lượng tổ hợp**

![Công thức](https://www.mathsisfun.com/combinatorics/images/combinations-repeat.gif)

Trong đó `n` là số lượng thứ để chọn từ, và chúng ta
chọn `r` trong số đó. Cho phép lặp lại,
thứ tự không quan trọng.

## Bảng Tóm Tắt

![Tổng quan về Hoán vị và Tổ hợp](./images/overview.png)

![Tổng quan về Tổ hợp](./images/combinations-overview.jpg)

|                                                                  |                                                                        |
| ---------------------------------------------------------------- | ---------------------------------------------------------------------- |
| ![Tổ hợp có lặp lại](./images/combinations-with-repetitions.jpg) | ![Tổ hợp không lặp lại](./images/combinations-without-repetitions.jpg) |

_Tạo với [okso.app](https://okso.app)_

## Tài liệu tham khảo

- [Math Is Fun](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)
- [Bảng Tóm Tắt Hoán vị/tổ hợp](https://medium.com/@trekhleb/permutations-combinations-algorithms-cheat-sheet-68c14879aba5)
