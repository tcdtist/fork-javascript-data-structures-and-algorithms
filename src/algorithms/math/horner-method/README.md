# Phương Pháp của Horner

_Xem bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong toán học, phương pháp của Horner (hoặc còn gọi là phương pháp Horner) là một thuật toán để tính giá trị của đa thức. Với phương pháp này, có thể tính giá trị của một đa thức chỉ với `n` phép cộng và `n` phép nhân. Do đó, yêu cầu lưu trữ của nó là `n` lần số bit của `x`.

Phương pháp của Horner có thể được dựa trên công thức sau đây:

![Quy tắc của Horner](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a576e42d875496f8b0f0dda5ebff7c2415532e4)

Công thức này được gọi là _quy tắc của Horner_.

Để giải quyết phần bên phải của công thức trên, với một `x` cụ thể, chúng ta bắt đầu bằng cách lặp qua đa thức từ bên trong ra ngoài, tích lũy kết quả của mỗi lần lặp. Sau `n` lần lặp, với `n` là bậc của đa thức, kết quả tích lũy sẽ cho chúng ta giá trị của đa thức.

**Sử dụng đa thức:**
`4 * x^4 + 2 * x^3 + 3 * x^2 + x^1 + 3`, một cách tiếp cận truyền thống để tính giá trị của nó tại `x = 2`, có thể được biểu diễn dưới dạng một mảng `[3, 1, 3, 2, 4]` và lặp qua nó, lưu mỗi giá trị lặp lại vào một biến tích lũy, ví dụ như `acc += pow(x=2, index) * array[index]`. Về bản chất, mỗi phép tính lũy thừa của một số (`pow`) đều có `n-1` phép nhân. Vì vậy, trong kịch bản này, tổng cộng sẽ có `14` phép tính đã xảy ra, bao gồm `4` phép cộng, `5` phép nhân và `5` phép lũy thừa (chúng ta giả định rằng mỗi lũy thừa được tính bằng cách nhân lặp lại).

Bây giờ, **sử dụng cùng một kịch bản nhưng với quy tắc của Horner**, đa thức có thể được viết lại thành `x * (x * (x * (4 * x + 2) + 3) + 1) + 3`, biểu diễn nó dưới dạng `[4, 2, 3, 1, 3]`, có thể lưu giá trị của lần lặp đầu tiên là `acc = arr[0] * (x=2) + arr[1]`, và sau đó kết thúc các lần lặp cho `acc *= (x=2) + arr[index]`. Trong cùng một kịch bản nhưng sử dụng quy tắc của Horner, tổng cộng sẽ có `10` phép tính đã xảy ra, bao gồm chỉ `4` phép cộng và `4` phép nhân.

## Tài Liệu Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Horner%27s_method)
