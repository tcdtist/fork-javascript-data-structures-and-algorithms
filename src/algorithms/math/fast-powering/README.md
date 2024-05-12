# Thuật toán lũy thừa nhanh

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Sức mạnh của một số** cho biết phải sử dụng số đó bao nhiêu lần trong một phép nhân.

Nó được viết dưới dạng một số nhỏ bên phải và phía trên số cơ bản.

![Lũy thừa](https://www.mathsisfun.com/algebra/images/exponent-8-2.svg)

## Độ phức tạp của thuật toán ngây thơ

Làm thế nào để tính `a` mũ `b`?

Chúng ta nhân `a` cho chính nó, `b` lần. Tức là, `a^b = a * a * a * ... * a` (`b` lần của `a`).

Phép tính này sẽ mất `O(n)` thời gian vì chúng ta cần thực hiện phép nhân chính xác `n` lần.

## Thuật toán lũy thừa nhanh

Liệu chúng ta có thể làm tốt hơn so với thuật toán ngây thơ không? Có, chúng ta có thể giải quyết bài toán lũy thừa trong thời gian `O(log(n))`.

Thuật toán sử dụng phương pháp chia để trị để tính lũy thừa. Hiện tại, thuật toán này hoạt động cho hai số nguyên dương `X` và `Y`.

Ý tưởng đằng sau thuật toán dựa trên sự thật rằng:

Đối với `Y` **chẵn**:

```text
X^Y = X^(Y/2) * X^(Y/2)
```

Đối với `Y` **lẻ**:

```text
X^Y = X^(Y//2) * X^(Y//2) * X
trong đó Y//2 là kết quả của phép chia của Y cho 2 mà không có phần dư.
```

**Ví dụ**

```text
2^4 = (2 * 2) * (2 * 2) = (2^2) * (2^2)
```

```text
2^5 = (2 * 2) * (2 * 2) * 2 = (2^2) * (2^2) * (2)
```

Bây giờ, vì ở mỗi bước chúng ta cần tính lũy thừa `X^(Y/2)` giống nhau hai lần, chúng ta có thể tối ưu hóa nó bằng cách lưu trữ vào một biến trung gian để tránh tính toán trùng lặp.

**Độ phức tạp thời gian**

Vì mỗi lần lặp chúng ta chia mũ cho hai, sau đó chúng ta sẽ gọi hàm đệ quy `log(n)` lần. Do đó, độ phức tạp thời gian của thuật toán được giảm xuống thành:

```text
O(log(n))
```

## Tham khảo

- [YouTube](https://www.youtube.com/watch?v=LUWavfN9zEo&index=80&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&t=0s)
- [Wikipedia](https://en.wikipedia.org/wiki/Exponentiation_by_squaring)
