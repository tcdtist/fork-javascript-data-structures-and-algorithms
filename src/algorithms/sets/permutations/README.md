# Hoán vị

_Đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Khi thứ tự không quan trọng, đó là một **Tổ hợp**.

Khi thứ tự **quan trọng**, đó là một **Hoán vị**.

**"Mật khẩu của két là 472"**. Chúng ta quan tâm đến thứ tự. `724` không hoạt động, cũng như `247`.
Nó phải chính xác là `4-7-2`.

## Hoán vị không lặp lại

Một hoán vị, còn được gọi là “số sắp xếp” hoặc “thứ tự”, là một sắp xếp lại của
các phần tử của một danh sách có thứ tự `S` thành một một-một tương ứng với `S` chính nó.

Dưới đây là các hoán vị của chuỗi `ABC`.

`ABC ACB BAC BCA CBA CAB`

Hoặc ví dụ về ba người đầu tiên trong một cuộc đua: bạn không thể là người đầu tiên và thứ hai.

**Số lượng tổ hợp**

```
n * (n-1) * (n -2) * ... * 1 = n!
```

## Hoán vị có lặp lại

Khi lặp lại được phép, chúng ta có các hoán vị có lặp lại.
Ví dụ, khóa dưới đây: nó có thể là `333`.

![Khóa hoán vị](https://www.mathsisfun.com/combinatorics/images/combination-lock.jpg)

**Số lượng tổ hợp**

```
n * n * n ... (r lần) = n^r
```

## Bảng tóm tắt

![Tổ hợp và Hoán vị Tổng quan](./images/overview.png)

![Tổ hợp Tổng quan](./images/permutations-overview.jpeg)

|                                                                   |                                                                         |
| ----------------------------------------------------------------- | ----------------------------------------------------------------------- |
| ![Hoán vị có lặp lại](./images/permutations-with-repetitions.jpg) | ![Hoán vị không lặp lại](./images/permutations-without-repetitions.jpg) |

_Tạo với [okso.app](https://okso.app)_

## Tài liệu tham khảo

- [Toán vui vẻ](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)
- [Tài liệu hỗ trợ hoán vị/tổ hợp](https://medium.com/@trekhleb/permutations-combinations-algorithms-cheat-sheet-68c14879aba5)
