# Phương pháp căn bậc hai (Phương pháp Newton)

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong phân tích số, một nhánh của toán học, có một số thuật toán hoặc phương pháp để tính căn bậc hai chính của một số thực không âm. Như, nói chung, các căn bậc của một hàm không thể tính chính xác. Các thuật toán tìm gốc cung cấp các xấp xỉ cho các căn được biểu diễn dưới dạng số dấu chấm động.

Việc tìm ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/bff86975b0e7944720b3e635c53c22c032a7a6f1) là
giống như giải phương trình ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/6cf57722151ef19ba1ca918d702b95c335e21cad) cho một
`x` dương. Do đó, bất kỳ thuật toán tìm gốc số nào cũng có thể được sử dụng.

**Phương pháp Newton** (còn được gọi là phương pháp Newton–Raphson), được đặt theo
_Isaac Newton_ và _Joseph Raphson_, là một ví dụ về một thuật toán tìm gốc. Đây là một
phương pháp để tìm các xấp xỉ tốt hơn đối với các gốc của một hàm có giá trị thực.

Hãy bắt đầu bằng cách giải thích ý tưởng chung của phương pháp Newton và sau đó áp dụng nó vào trường hợp cụ thể của chúng ta với việc tìm căn bậc hai của số.

## Ý tưởng chung của Phương pháp Newton

Phương pháp Newton–Raphson trong một biến được thực hiện như sau:

Phương pháp bắt đầu với một hàm `f` được xác định trên các số thực `x`, đạo hàm của hàm `f` `f'`, và một
đoán đầu `x0` cho một gốc của hàm `f`. Nếu hàm thỏa mãn các giả định được đưa ra trong công thức và đoán đầu tiên gần, thì xấp xỉ tốt hơn `x1` là:

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/52c50eca0b7c4d64ef2fdca678665b73e944cb84)

Hình học, `(x1, 0)` là sự giao nhau của trục `x` và tiếp tuyến của đồ thị của `f` tại `(x0, f (x0))`.

Quá trình được lặp lại như sau:

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/710c11b9ec4568d1cfff49b7c7d41e0a7829a736)

cho đến khi đạt được giá trị đủ chính xác.

![](https://upload.wikimedia.org/wikipedia/commons/e/e0/NewtonIteration_Ani.gif)

## Phương pháp Newton để Tìm Căn bậc hai

Như đã đề cập ở trên, việc tìm ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/bff86975b0e7944720b3e635c53c22c032a7a6f1) là
giống như giải phương trình ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/6cf57722151ef19ba1ca918d702b95c335e21cad) cho một
`x` dương.

Đạo hàm của hàm `f(x)` trong trường hợp của vấn đề căn bậc hai là `2x`.

Sau khi áp dụng công thức Newton (xem ở trên) chúng ta có phương trình sau cho các lần lặp của thuật toán:

```text
x := x - (x² - S) / (2x)
```

Phần `x² − S` ở trên là khoảng cách `x²` so với nơi cần phải đến, và phép chia cho `2x` là đạo hàm của `x²`, để tỷ lệ điều chỉnh `x` bằng cách nhanh chóng `x²` đang thay đổi.

## Tham khảo

- [Các phương pháp tính căn bậc hai trên Wikipedia](https://en.wikipedia.org/wiki/Methods_of_computing_square_roots)
- [Phương pháp Newton trên Wikipedia](https://en.wikipedia.org/wiki/Newton%27s_method)
