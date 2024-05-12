# Khoảng cách Levenshtein

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Khoảng cách Levenshtein là một chỉ số chuỗi để đo sự khác biệt giữa hai chuỗi. Một cách không chính thức, khoảng cách Levenshtein giữa hai từ là số lượng tối thiểu các chỉnh sửa đơn vị (chèn, xóa hoặc thay thế một ký tự) cần thiết để biến đổi một từ thành từ kia.

## Định nghĩa

Toán học, khoảng cách Levenshtein giữa hai chuỗi `a` và `b` (có độ dài `|a|` và `|b|` tương ứng) được cho bởi
![Levenshtein](https://wikimedia.org/api/rest_v1/media/math/render/svg/4cf357d8f2135035207088d2c7b890fb4b64e410)
trong đó

![Levenshtein](https://wikimedia.org/api/rest_v1/media/math/render/svg/f0a48ecfc9852c042382fdc33c19e11a16948e85)

với
![Levenshtein](https://wikimedia.org/api/rest_v1/media/math/render/svg/52512ede08444b13838c570ba4a3fc71d54dbce9)
là hàm chỉ số bằng `0` khi
![Levenshtein](https://wikimedia.org/api/rest_v1/media/math/render/svg/231fda9ee578f0328c5ca28088d01928bb0aaaec)
và bằng 1 trong trường hợp ngược lại, và
![Levenshtein](https://wikimedia.org/api/rest_v1/media/math/render/svg/bdc0315678caad28648aafedb6ebafb16bd1655c)
là khoảng cách giữa `i` ký tự đầu tiên của `a` và `j` ký tự đầu tiên của `b`.

Lưu ý rằng phần tử đầu tiên trong giá trị tối thiểu tương ứng với việc xóa (từ `a` thành `b`), phần thứ hai là chèn và phần thứ ba là khớp hoặc không khớp, phụ thuộc vào việc các ký tự tương ứng có giống nhau không.

## Ví dụ

Ví dụ, khoảng cách Levenshtein giữa `kitten` và `sitting` là `3`, vì ba chỉnh sửa sau đây biến đổi một thành cái kia, và không có cách nào làm điều này ít hơn ba chỉnh sửa:

1. **k**itten → **s**itten (thay thế "s" bằng "k")
2. sitt**e**n → sitt**i**n (thay thế "i" bằng "e")
3. sittin → sittin**g** (chèn "g" vào cuối).

## Ứng dụng

Điều này có một loạt các ứng dụng, ví dụ như kiểm tra chính tả, hệ thống sửa lỗi cho nhận dạng ký tự quang học, tìm kiếm chuỗi mờ và phần mềm hỗ trợ dịch thuật ngôn ngữ tự nhiên dựa trên bộ nhớ dịch.

## Giải thích phương pháp lập trình động

Hãy xem một ví dụ đơn giản về việc tìm khoảng cách chỉnh sửa tối thiểu giữa các chuỗi `ME` và `MY`. Theo cách hiểu của bạn, bạn đã biết rằng khoảng cách chỉnh sửa tối thiểu ở đây là `1` thao tác, đó là thay thế `E` bằng `Y`. Nhưng hãy cố gắng hình thành nó dưới dạng thuật toán để có thể thực hiện các ví dụ phức tạp hơn như biến đổi `Saturday` thành `Sunday`.

Để áp dụng công thức toán học được đề cập ở trên vào biến đổi `ME → MY`, chúng ta cần biết khoảng cách chỉnh sửa tối thiểu của các biến đổi `ME → M`, `M → MY` và `M → M` trước. Sau đó, chúng ta sẽ cần chọn cái nhỏ nhất và thêm _một_ thao tác để biến đổi các ký tự cuối cùng `E → Y`. Vì vậy, khoảng cách chỉnh sửa tối thiểu của biến đổi `ME → MY` được tính dựa trên ba biến đổi có thể trước đó.

Để giải thích điều này cụ thể hơn, hãy vẽ ma trận sau:

![Ma trận Levenshtein](https://cdn-images-1.medium.com/max/1600/1*aTunSUoy0BJyYBVn4tWGrA.png)

- Ô `(0:1)` chứa số 1 màu đỏ. Nó có nghĩa là chúng ta cần 1 thao tác để biến đổi `M` thành một chuỗi trống. Và đó là bằng cách xóa `M`. Đây là lý do tại sao số này màu đỏ.
- Ô `(0:2)` chứa số 2 màu đỏ. Nó có nghĩa là chúng ta cần 2 thao tác để biến đổi `ME` thành một chuỗi trống. Và đó là bằng cách xóa `E` và `M`.
- Ô `(1:0)` chứa số 1 màu xanh. Nó có nghĩa là chúng ta cần 1 thao tác để biến đổi một chuỗi trống thành `M`. Và đó là bằng cách chèn `M`. Đây là lý do tại sao số này màu xanh.
- Ô `(2:0)` chứa số 2 màu xanh. Nó có nghĩa là chúng ta cần 2 thao tác để biến đổi một chuỗi trống thành `MY`. Và đó là bằng cách chèn `Y` và `M`.
- Ô `(1:1)` chứa số 0. Nó có nghĩa là không tốn gì
  để biến đổi `M` thành `M`.
- Ô `(1:2)` chứa số 1 màu đỏ. Nó có nghĩa là chúng ta cần 1 thao tác
  để biến đổi `ME` thành `M`. Và đó là bằng cách xóa `E`.
- Và tiếp tục...

Điều này trông dễ dàng cho ma trận nhỏ như của chúng ta (chỉ là `3x3`). Nhưng ở đây, bạn có thể tìm thấy các khái niệm cơ bản có thể được áp dụng để tính toán tất cả các số đó cho các ma trận lớn hơn (ví dụ, một ma trận `9x7` cho biến đổi `Saturday → Sunday`).

Theo công thức, bạn chỉ cần ba ô liền kề `(i-1:j)`, `(i-1:j-1)`, và `(i:j-1)` để tính toán số cho ô hiện tại `(i:j)`. Tất cả những gì chúng ta cần làm là tìm số nhỏ nhất của ba ô đó, sau đó thêm `1` trong trường hợp nếu chúng ta có các chữ cái khác nhau trong hàng `i` và cột `j`.

Bạn có thể thấy rõ tính đệ quy của vấn đề.

Hãy vẽ một biểu đồ quyết định cho vấn đề này.

![Biểu đồ Quyết định Khoảng cách chỉnh sửa tối thiểu](https://cdn-images-1.medium.com/max/1600/1*8jD0qvr5B9PwRFM_9z7q9A.png)

Bạn có thể thấy một số vấn đề con chồng chéo trên hình ảnh được đánh dấu
bằng màu đỏ. Ngoài ra, không có cách nào để giảm số lượng thao tác và làm
nó ít hơn một tối thiểu của ba ô liền kề đó từ công thức.

Bạn cũng có thể nhận thấy rằng mỗi số ô trong ma trận đều được tính toán
dựa trên các ô trước đó. Do đó, kỹ thuật bảng trên (điền vào bộ nhớ đệm theo
hướng từ dưới lên) được áp dụng ở đây.

Áp dụng nguyên tắc này tiếp tục, chúng ta có thể giải quyết các trường hợp
phức tạp hơn như với biến đổi `Saturday → Sunday`.

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Levenshtein_distance)
- [YouTube](https://www.youtube.com/watch?v=We3YDTzNXEk&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [ITNext](https://itnext.io/dynamic-programming-vs-divide-and-conquer-2fea680becbe)
