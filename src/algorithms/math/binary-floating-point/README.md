# Biểu diễn nhị phân của số dấu chấm động

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Bạn có bao giờ tự hỏi là máy tính lưu trữ các số dấu chấm động như `3.1416` (𝝿) hoặc `9.109 × 10⁻³¹` (khối lượng của electron tính bằng kg) trong bộ nhớ có hạn bởi một số hữu hạn các số một và số không (còn gọi là bit) không?

Có vẻ khá đơn giản đối với số nguyên (ví dụ: `17`). Hãy nói chúng ta có 16 bit (2 byte) để lưu trữ số. Trong 16 bit, chúng ta có thể lưu trữ số nguyên trong một phạm vi `[0, 65535]`:

```text
(0000000000000000)₂ = (0)₁₀

(0000000000010001)₂ =
    (1 × 2⁴) +
    (0 × 2³) +
    (0 × 2²) +
    (0 × 2¹) +
    (1 × 2⁰) = (17)₁₀

(1111111111111111)₂ =
    (1 × 2¹⁵) +
    (1 × 2¹⁴) +
    (1 × 2¹³) +
    (1 × 2¹²) +
    (1 × 2¹¹) +
    (1 × 2¹⁰) +
    (1 × 2⁹) +
    (1 × 2⁸) +
    (1 × 2⁷) +
    (1 × 2⁶) +
    (1 × 2⁵) +
    (1 × 2⁴) +
    (1 × 2³) +
    (1 × 2²) +
    (1 × 2¹) +
    (1 × 2⁰) = (65535)₁₀
```

Nếu chúng ta cần một số nguyên có dấu, chúng ta có thể sử dụng [bù hai](https://en.wikipedia.org/wiki/Two%27s_complement) và dịch phạm vi từ `[0, 65535]` sang các số âm. Trong trường hợp này, 16 bit của chúng ta sẽ biểu diễn các số trong phạm vi `[-32768, +32767]`.

Như bạn có thể đã nhận thấy, phương pháp này sẽ không cho phép bạn biểu diễn các số như `-27.15625` (các số sau dấu thập phân đơn giản chỉ bị bỏ qua).

Tuy nhiên, chúng ta không phải là những người đầu tiên nhận thấy vấn đề này. Khoảng ≈36 năm trước, một số người thông minh đã vượt qua hạn chế này bằng cách giới thiệu tiêu chuẩn [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754) cho phép tính toán số dấu chấm động.

Tiêu chuẩn IEEE 754 mô tả cách (khung) sử dụng các 16 bit đó (hoặc 32, hoặc 64 bit) để lưu trữ các số có phạm vi rộng hơn, bao gồm cả các số dấu chấm động nhỏ (nhỏ hơn 1 và gần với 0).

Để hiểu ý tưởng sau tiêu chuẩn, chúng ta có thể nhớ lại [cách biểu diễn khoa học](https://en.wikipedia.org/wiki/Scientific_notation) - cách biểu diễn các số quá lớn hoặc quá nhỏ (thường sẽ cho ra một chuỗi số dài) để viết dễ dàng hơn trong dạng thập phân.

![Biểu diễn số học](images/03-scientific-notation.png)

Như bạn có thể thấy từ hình ảnh, biểu diễn số có thể được chia thành ba phần:

- **dấu**
- \*\*phân số (còn gọi là phần quan trọng)\*\* - các chữ số có giá trị (ý nghĩa, dữ liệu) của số

- **số mũ** - điều khiển việc di chuyển dấu thập phân ở phân số ra xa và theo hướng nào

Phần **cơ số** chúng ta có thể bỏ qua bằng cách đồng ý về giá trị của nó. Trong trường hợp của chúng tôi, chúng tôi sẽ sử dụng `2` làm cơ số.

Thay vì sử dụng tất cả 16 bit (hoặc 32 bit, hoặc 64 bit) để lưu trữ phần phân số của số, chúng ta có thể chia sẻ các bit và lưu trữ dấu, số mũ và phân số cùng một lúc. Tùy thuộc vào số bit mà chúng ta sẽ sử dụng để lưu trữ số, chúng ta sẽ có các phân chia như sau:

| Định dạng số dấu chấm động                                                               | Tổng số bit | Số bit dấu | Số bit số mũ | Số bit phân số | Cơ số |
| :--------------------------------------------------------------------------------------- | :---------: | :--------: | :----------: | :------------: | :---: |
| [Nửa độ chính xác](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)   |     16      |     1      |      5       |       10       |   2   |
| [Đơn độ chính xác](https://en.wikipedia.org/wiki/Single-precision_floating-point_format) |     32      |     1      |      8       |       23       |   2   |
| [Đôi độ chính xác](https://en.wikipedia.org/wiki/Double-precision_floating-point_format) |     64      |     1      |      11      |       52       |   2   |

Với cách tiếp cận này, số lượng bit cho phần phân số đã được giảm (ví dụ: đối với số 16 bit, nó đã được giảm từ 16 bit xuống còn 10 bit). Điều này có nghĩa là phần phân số có thể có một phạm vi giá trị hẹp hơn bây giờ (mất một số độ chính xác). Tuy nhiên, vì chúng ta cũng có một phần số mũ, điều này thực sự sẽ tăng phạm vi số cuối cùng và cũng cho phép chúng ta mô tả các số giữa 0 và 1 (nếu số mũ là âm).

> Ví dụ, một biến số nguyên có dấu 32 bit có giá trị tối đa là 2³¹ − 1 = 2,147,483,647, trong khi một biến số dấu chấm động 32 bit theo chuẩn IEEE 754 có giá trị tối đa là ≈ 3.4028235 × 10³⁸.

Để có thể có số mũ âm, tiêu chuẩn IEEE 754 sử dụng [số mũ lệch](https://en.wikipedia.org/wiki/Exponent_bias). Ý tưởng đơn giản - trừ bias từ giá trị số mũ để làm cho nó trở thành số mũ âm. Ví dụ, nếu số mũ có 5 bit, nó có thể lấy các giá trị từ phạm vi `[0, 31]` (tất cả các giá trị ở đây đều là dương). Nhưng nếu chúng ta trừ giá trị `15` từ đó, phạm vi sẽ là `[-15, 16]`. Số `15` được gọi là bias, và nó được tính bằng công thức sau:

```
số mũ lệch = 2 ^ (k−1) − 1

k - số bit số mũ
```

Tôi đã cố gắng mô tả logic sau việc chuyển đổi số dấu chấm động từ dạng nhị phân trở lại dạng thập phân trên hình ảnh dưới đây. Hy vọng, điều này sẽ giúp bạn hiểu rõ hơn về cách tiêu chuẩn IEEE 754 hoạt động. Số 16 bit được sử dụng ở đây để đơn giản hóa, nhưng cách tiếp cận tương tự cũng hoạt động cho các số 32 bit và 64 bit.

![Định dạng số dấu chấm động nửa độ chính xác được giải thích trong một hình ảnh](images/02-half-precision-floating-point-number-explained.png)

> Kiểm tra [phiên bản tương tác của biểu đồ này](https://trekhleb.dev/blog/2021/binary-floating-point/) để chơi với việc thiết lập bit bật và tắt, và xem làm thế nào nó sẽ ảnh hưởng đến kết quả cuối cùng

Dưới đây là phạm vi số mà các định dạng số dấu chấm động khác nhau hỗ trợ:

| Định dạng số dấu chấm động | Số mũ tối thiểu | Số mũ tối đa | Phạm vi | Số dương nhỏ nhất |
| :------------------------- | :-------------- | :----------- | :------ | :---------------- |
| Nửa độ chính xác           | −14             | +15          | ±65,504 | 6.10 ×            |

10⁻⁵ |
| Đơn độ chính xác | −126 | +127 | ±3.4028235 × 10³⁸ | 1.18 × 10⁻³⁸ |

Hãy nhớ rằng đây hoàn toàn không phải là một cái nhìn toàn diện và đầy đủ về tiêu chuẩn IEEE 754. Đây thực sự là một cái nhìn tổng quan và đơn giản. Một số trường hợp cụ thể đã bị bỏ qua trong các ví dụ trên để đơn giản hóa trong quá trình trình bày (ví dụ: `-0`, `-∞`, `+∞` và giá trị `NaN` (không phải là một số))

## Ví dụ mã

- Xem tệp [bitsToFloat.js](bitsToFloat.js) để xem ví dụ về cách chuyển đổi mảng bit thành số dấu chấm động (ví dụ này hơi nhân tạo nhưng vẫn cho cái nhìn tổng quan về cách chuyển đổi đang diễn ra)
- Xem tệp [floatAsBinaryString.js](floatAsBinaryString.js) để xem ví dụ về cách xem biểu diễn nhị phân thực sự của số dấu chấm động trong JavaScript

## Tham khảo

Bạn cũng có thể muốn kiểm tra các tài nguyên sau để hiểu sâu hơn về biểu diễn nhị phân của số dấu chấm động:

- [Phiên bản tương tác của bài viết này](https://trekhleb.dev/blog/2021/binary-floating-point/) (cho phép thiết lập các bit bật và tắt thủ công và xem số dấu chấm động kết quả)
- [Đây là những gì bạn cần biết về kiểu số JavaScript](https://indepth.dev/posts/1139/here-is-what-you-need-to-know-about-javascripts-number-type)
- [Float Exposed](https://float.exposed/)
- [Trực quan hóa IEEE754](https://bartaz.github.io/ieee754-visualization/)
