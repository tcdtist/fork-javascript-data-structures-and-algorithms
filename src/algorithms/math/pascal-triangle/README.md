# Tam giác Pascal

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong toán học, **tam giác Pascal** là một mảng tam giác của [hệ số nhị thức](https://en.wikipedia.org/wiki/Binomial_coefficient).

Các hàng của tam giác Pascal thường được đánh số từ hàng `n = 0` ở phía trên cùng (hàng `0`). Các phần tử trong mỗi hàng được đánh số từ trái sang phải, bắt đầu từ `k = 0` và thường được xếp lệch so với các số trong các hàng liền kề. Tam giác có thể được xây dựng theo cách sau: Ở hàng `0` (hàng trên cùng), có một phần tử duy nhất khác `0` là `1`. Mỗi phần tử của mỗi hàng tiếp theo được xây dựng bằng cách cộng số phía trên bên trái với số phía trên bên phải, coi các phần tử trống như `0`. Ví dụ, số ban đầu trong hàng đầu tiên (hoặc bất kỳ hàng nào khác) là `1` (tổng của `0` và `1`), trong khi số `1` và `3` trong hàng thứ ba được cộng lại để tạo ra số `4` trong hàng thứ tư.

![Tam giác Pascal](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

## Công thức

Phần tử ở hàng thứ `n` và cột thứ `k` của tam giác Pascal được ký hiệu là ![Công thức](https://wikimedia.org/api/rest_v1/media/math/render/svg/206415d3742167e319b2e52c2ca7563b799abad7). Ví dụ, phần tử duy nhất khác `0` trong hàng trên cùng là ![Ví dụ về công thức](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7e35f86368d5978b46c07fd6dddca86bd6e635c).

Với ký hiệu này, việc xây dựng trong đoạn trước có thể được viết như sau:

![Công thức](https://wikimedia.org/api/rest_v1/media/math/render/svg/203b128a098e18cbb8cf36d004bd7282b28461bf)

cho mọi số nguyên không âm `n` và mọi số nguyên `k` nằm giữa `0` và `n`, bao gồm cả `0` và `n`.

![Hệ số nhị thức](https://wikimedia.org/api/rest_v1/media/math/render/svg/a2457a7ef3c77831e34e06a1fe17a80b84a03181)

## Tính các phần tử trong tam giác trong thời gian O(n)

Chúng ta biết rằng phần tử thứ `i` trong hàng số `lineNumber` là Hệ số nhị thức `C(lineNumber, i)` và tất cả các hàng bắt đầu với giá trị `1`. Ý tưởng là tính `C(lineNumber, i)` bằng cách sử dụng `C(lineNumber, i-1)`. Nó có thể được tính trong thời gian `O(1)` bằng cách sau:

```
C(lineNumber, i)   = lineNumber! / ((lineNumber - i)! * i!)
C(lineNumber, i - 1) = lineNumber! / ((lineNumber - i + 1)! * (i - 1)!)
```

Chúng ta có thể suy ra biểu thức sau từ hai biểu thức trên:

```
C(lineNumber, i) = C(lineNumber, i - 1) * (lineNumber - i + 1) / i
```

Vì vậy, `C(lineNumber, i)` có thể được tính từ `C(lineNumber, i - 1)` trong thời gian `O(1)`.

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Pascal%27s_triangle)
- [GeeksForGeeks](https://www.geeksforgeeks.org/pascal-triangle/)
