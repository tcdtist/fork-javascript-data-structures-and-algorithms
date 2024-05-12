# Số Phức

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Một **số phức** là một số có thể được biểu diễn dưới dạng `a + b * i`, trong đó `a` và `b` là các số thực, và `i` là một giải pháp của phương trình `x^2 = −1`. Vì không có _số thực_ nào thỏa mãn phương trình này, `i` được gọi là một _số ảo_. Đối với số phức `a + b * i`, `a` được gọi là _phần thực_, và `b` được gọi là _phần ảo_.

![Số Phức](https://www.mathsisfun.com/numbers/images/complex-example.svg)

Một Số Phức là sự kết hợp của một Số Thực và một Số Ảo:

![Số Phức](https://www.mathsisfun.com/numbers/images/complex-number.svg)

Về mặt hình học, số phức mở rộng khái niệm của đường số một chiều sang _mặt phẳng phức hai chiều_ bằng cách sử dụng trục hoành cho phần thực và trục tung cho phần ảo. Số phức `a + b * i` có thể được xác định với điểm `(a, b)` trên mặt phẳng phức.

Một số phức có phần thực bằng không được gọi là _số ảo tuyệt đối_; các điểm cho những số này nằm trên trục thẳng đứng của mặt phẳng phức. Một số phức có phần ảo bằng không có thể được xem như một _số thực_; điểm của nó nằm trên trục hoành của mặt phẳng phức.

| Số Phức | Phần Thực | Phần Ảo |              |
| :------ | :-------: | :-----: | ------------ |
| 3 + 2i  |     3     |    2    |              |
| 5       |     5     |  **0**  | Ảo Tuyệt Đối |
| −6i     |   **0**   |   -6    | Ảo Tuyệt Đối |

Một số phức có thể được biểu diễn hình thức bằng cách sử dụng một cặp số `(a, b)` tạo thành một vector trên một biểu đồ gọi là _biểu đồ Argand_, đại diện cho _mặt phẳng phức_. `Re` là trục thực, `Im` là trục ảo, và `i` thỏa mãn `i^2 = −1`.

![Số Phức](https://upload.wikimedia.org/wikipedia/commons/a/af/Complex_number_illustration.svg)

> Số phức không có nghĩa là phức tạp. Nó có nghĩa là hai loại số, thực và ảo,
> cùng tạo thành một số phức, giống như một khu phức hợp (những tòa nhà
> được kết nối với nhau).

## Dạng Cực

Một cách khác để định nghĩa một điểm `P` trong mặt phẳng phức, ngoài việc sử dụng
các tọa độ x và y, là sử dụng khoảng cách từ điểm `O`, điểm
có tọa độ `(0, 0)` (nguồn gốc), cùng với góc được chia đều
giữa trục thực dương và đoạn thẳng `OP` theo hướng ngược chiều kim đồng hồ. Ý tưởng này dẫn đến dạng cực của số phức.

![Dạng Cực](https://upload.wikimedia.org/wikipedia/commons/7/7a/Complex_number_illustration_modarg.svg)

Giá trị tuyệt đối (hoặc độ lớn) của một số phức `z = x + yi` là:

![Bán Kính](https://wikimedia.org/api/rest_v1/media/math/render/svg/b59629c801aa0ddcdf17ee489e028fb9f8d4ea75)

Góc của `z` (trong nhiều ứng dụng được gọi là "pha") là góc
của bán kính `OP` với trục thực dương, và được viết dưới dạng `arg(z)`. Như
với giá trị tuyệt đối, góc có thể được tìm từ dạng hình chữ nhật `x+yi`:

![Góc](https://wikimedia.org/api/rest_v1/media/math/render/svg/7cbbdd9bb1dd5df86dd2b820b20f82995023e566)

Cả `r` và `φ` cùng cung cấp một cách khác để biểu diễn số phức, là
dạng cực, vì sự kết hợp của độ lớn và góc hoàn toàn xác định vị trí
của một điểm trên mặt phẳng. Việc khôi phục lại các tọa độ hình chữ nhật ban đầu từ dạng cực được thực hiện thông qua công thức gọi là dạng lượng giác:

![Dạng Cực](https://wikimedia.org/api/rest_v1/media/math/render/svg/b03de1e1b7b049880b5e4870b68a57bc180ff6ce)

Sử dụng công thức Euler, điều này có thể được viết dưới dạng:

![Dạng Euler](https://wikimedia.org/api/rest_v

1/media/math/render/svg/0a087c772212e7375cb321d83fc1fcc715cd0ed2)

## Các Phép Tính Cơ Bản

### Cộng

Để cộng hai số phức, chúng ta cộng từng phần một riêng lẻ:

```text
(a + b * i) + (c + d * i) = (a + c) + (b + d) * i
```

**Ví dụ**

```text
(3 + 5i) + (4 − 3i) = (3 + 4) + (5 − 3)i = 7 + 2i
```

Trên mặt phẳng phức, phép cộng sẽ trông như sau:

![Cộng Số Phức](https://www.mathsisfun.com/algebra/images/complex-plane-vector-add.svg)

### Trừ

Để trừ hai số phức, chúng ta trừ từng phần một riêng lẻ:

```text
(a + b * i) - (c + d * i) = (a - c) + (b - d) * i
```

**Ví dụ**

```text
(3 + 5i) - (4 − 3i) = (3 - 4) + (5 + 3)i = -1 + 8i
```

### Nhân

Để nhân số phức, mỗi phần của số phức đầu tiên được nhân
với mỗi phần của số phức thứ hai:

Chỉ cần sử dụng "FOIL", viết tắt của "**F**irsts, **O**uters, **I**nners, **L**asts"
(see [Nhân Đa Thức](https://www.mathsisfun.com/algebra/polynomials-multiplying.html) để
biết thêm chi tiết):

![Nhân Số Phức](https://www.mathsisfun.com/algebra/images/foil-complex.svg)

- Firsts: `a × c`
- Outers: `a × di`
- Inners: `bi × c`
- Lasts: `bi × di`

Nhìn chung, nó trông như thế này:

```text
(a + bi)(c + di) = ac + adi + bci + bdi^2
```

Nhưng cũng có một cách nhanh hơn!

Sử dụng quy tắc này:

```text
(a + bi)(c + di) = (ac − bd) + (ad + bc)i
```

**Ví dụ**

```text
(3 + 2i)(1 + 7i)
= 3×1 + 3×7i + 2i×1+ 2i×7i
= 3 + 21i + 2i + 14i^2
= 3 + 21i + 2i − 14   (bởi vì i^2 = −1)
= −11 + 23i
```

```text
(3 + 2i)(1 + 7i) = (3×1 − 2×7) + (3×7 + 2×1)i = −11 + 23i
```

### Phức Hợp

Chúng ta sẽ cần biết về phức hợp trong một phút nữa!

Phức hợp là khi chúng ta thay đổi dấu ở giữa như thế này:

![Phức Hợp Số Phức](https://www.mathsisfun.com/numbers/images/complex-conjugate.svg)

Một phức hợp thường được viết với một dấu than trên:

```text
______
5 − 3i   =   5 + 3i
```

Trên mặt phẳng phức, số phức phức hợp sẽ được phản chiếu qua trục số thực.

![Phức Hợp Số Phức](https://upload.wikimedia.org/wikipedia/commons/6/69/Complex_conjugate_picture.svg)

### Chia

Phức hợp được sử dụng để giúp phép chia số phức.

Mánh là _nhân cả trên và dưới với phức hợp của dưới_.

**Ví dụ**

```text
2 + 3i
------
4 − 5i
```

Nhân cả trên và dưới với phức hợp của `4 − 5i`:

```text
  (2 + 3i) * (4 + 5i)   8 + 10i + 12i + 15i^2
= ------------------- = ----------------------
  (4 − 5i) * (4 + 5i)   16 + 20i − 20i − 25i^2
```

Bây giờ hãy nhớ rằng `i^2 = −1`, vì vậy:

```text
  8 + 10i + 12i − 15    −7 + 22i   −7   22
= ------------------- = -------- = -- + -- * i
  16 + 20i − 20i + 25      41      41   41

```

Tuy nhiên, có một cách nhanh hơn.

Trong ví dụ trước, điều gì đã xảy ra ở dưới là thú vị:

```text
(4 − 5i)(4 + 5i) = 16 + 20i − 20i − 25i
```

Các thuật ngữ giữa `(20i − 20i)` bị loại bỏ! Hơn nữa, `i^2 = −1` nên chúng ta kết thúc với điều này:

```text
(4 − 5i)(4 + 5i) = 4^2 + 5^2
```

Điều này thực sự là một kết quả khá đơn giản. Quy tắc chung là:

```text
(a + bi)(a − bi) = a^2 + b^2
```

## Tài Liệu Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Complex_number)
- [Math is Fun](https://www.mathsisfun.com/numbers/complex-numbers.html)
