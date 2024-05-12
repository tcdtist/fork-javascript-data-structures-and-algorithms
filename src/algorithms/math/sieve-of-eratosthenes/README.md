# Sieve of Eratosthenes - Sàng Eratosthenes

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Sàng Eratosthenes là một thuật toán để tìm tất cả các số nguyên tố đến một giới hạn `n` nào đó.

Thuật toán này được cho là của Eratosthenes, một nhà toán học cổ Hy Lạp.

## Cách hoạt động

1. Tạo một mảng boolean có `n + 1` vị trí (để biểu diễn các số từ `0` đến `n`)
2. Đặt các vị trí `0` và `1` thành `false`, và các vị trí còn lại thành `true`
3. Bắt đầu từ vị trí `p = 2` (số nguyên tố đầu tiên)
4. Đánh dấu các bội số của `p` là `false` (tức là, các vị trí `2 * p`, `3 * p`, `4 * p`... cho đến khi bạn đạt đến cuối mảng)
5. Tìm vị trí đầu tiên lớn hơn `p` mà là `true` trong mảng. Nếu không có vị trí nào như vậy, dừng lại. Nếu có, gán `p` bằng số này (là số nguyên tố tiếp theo), và lặp lại từ bước 4

Khi thuật toán kết thúc, các số còn lại là `true` trong mảng là tất cả các số nguyên tố nhỏ hơn `n`.

Một cải tiến của thuật toán này là, ở bước 4, bắt đầu đánh dấu các bội số của `p` từ `p * p`, và không phải từ `2 * p`. Lý do tại sao điều này hoạt động là vì, tại thời điểm đó, các bội số nhỏ hơn của `p` đã được đánh dấu `false`.

## Ví dụ

![Sàng](https://upload.wikimedia.org/wikipedia/commons/b/b9/Sieve_of_Eratosthenes_animation.gif)

## Độ phức tạp

Thuật toán có độ phức tạp là `O(n log(log n))`.

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)
