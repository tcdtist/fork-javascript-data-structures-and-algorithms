# Thuật toán π của Liu Hui

_Xem bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong bình luận của mình về Tám Chương về Nghệ Thuật Toán Học,
Liu Hui đã chú ý rằng tỉ lệ của chu vi của một hình lục giác nội tiếp với đường
kính của hình tròn là `ba`, vì vậy `π` phải lớn hơn ba. Ông tiếp tục cung cấp
một mô tả chi tiết từng bước của một thuật toán lặp để tính `π` với
bất kỳ độ chính xác cần thiết dựa trên việc chia đôi các đa giác; ông tính `π` tới
từ `3.141024` đến `3.142708` với một hình 96 cạnh; ông đề xuất rằng `3.14`
là một xấp xỉ đủ tốt, và diễn đạt `π` là `157/50`; ông thừa nhận rằng
số này nhỏ hơn một chút. Sau đó, ông đã phát minh ra một phương pháp nhanh chóng và
tinh tế để cải thiện nó, và thu được `π ≈ 3.1416` chỉ với một hình 96 cạnh, với một độ chính xác
tương đương với một hình 1536 cạnh. Đó là đóng góp quan trọng nhất của ông trong
lĩnh vực này là thuật toán `π` lặp lại đơn giản của ông.

## Diện tích của một hình tròn

Liu Hui lập luận:

> Nhân một cạnh của một hình lục giác với bán kính (của nó
> vòng ngoài), sau đó nhân tiếp điều này với ba, để thu được
> diện tích của một hình đa giác dodecagon; nếu chúng ta chia một hình lục giác thành
> dodecagon, nhân cạnh của nó với bán kính của nó, sau đó lại
> nhân với sáu, chúng ta thu được diện tích của một hình đa giác 24 cạnh; càng tinh tế
> chúng ta cắt, mất mát càng nhỏ so với diện tích
> của hình tròn, do đó với mỗi lần cắt sau, diện tích của
> hình đa giác kết quả sẽ trùng khớp và trở thành một với
> hình tròn; không có mất mát nào sẽ xảy ra

![Liu Hui](https://upload.wikimedia.org/wikipedia/commons/6/69/Cutcircle2.svg)

Phương pháp của Liu Hui để tính diện tích của một hình tròn.

Hơn nữa, Liu Hui chứng minh rằng diện tích của một hình tròn bằng một nửa chu vi của nó
nhân với bán kính của nó. Ông nói:

> Giữa một đa giác và một hình tròn, có sự dư thừa về bán kính. Nhân sự
> dư thừa bán kính với một cạnh của đa giác. Kết quả là diện tích vượt quá biên của
> hình tròn

Trong biểu đồ `d = dư thừa bán kính`. Nhân `d` với một cạnh sẽ dẫn đến
hình chữ nhật `ABCD` vượt quá biên của hình tròn. Nếu một cạnh của đa giác
nhỏ (tức là có một số lượng rất lớn các cạnh), thì dư thừa bán kính
sẽ nhỏ, do đó diện tích dư thừa sẽ nhỏ.

> Nhân một cạnh của một đa giác với bán kính của nó, và diện tích tăng gấp đôi;
> do đó nhân nửa chu vi với bán kính để thu được diện tích của hình tròn.

![Liu Hui](https://upload.wikimedia.org/wikipedia/commons/9/95/Cutcircle.svg)

Diện tích bên trong một hình tròn bằng cách nhân bán kính với một nửa của
chu vi, hoặc `A = r x C/2 = r x r x π`.

## Thuật toán lặp lại

Liu Hui bắt đầu với một hình lục giác nội tiếp. Hãy cho `M` là chiều dài của một cạnh `AB` của
hình lục giác, `r` là bán kính của hình tròn.

![Liu Hui](https://upload.wikimedia.org/wikipedia/commons/4/46/Liuhui_geyuanshu.svg)

Chia `AB` đôi với đoạn thẳng `OPC`, `AC` trở thành một cạnh của dodecagon (12 cạnh), hãy
chiều dài của nó là `m`. Hãy cho chiều dài của `PC` là `j` và chiều dài của `OP` là `G`.

`AOP`, `APC` là hai tam giác vuông. Liu Hui đã sử dụng
[Định lý Gou Gu](https://en.wikipedia.org/wiki/Pythagorean_theorem) (Định lý Pythagoras)
lặp đi lặp lại:

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/dbfc192c78539c3901c7bad470302ededb76f813)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/ccd12a402367c2d6614c88e75006d50bfc3a9929)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/65d77869fc02c302d2d46d45f75ad7e79ae524fb)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/a7a0d0d7f505a0f434e5dd80c2fef6d2b30d6100)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/c31b9acf38f9d1a248d4023c3bf286bd03007f37)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/0dee798efb0b1e3e64d6b3542106cb3ecaa4a383)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/3ffeafe88d2983b364ad3442746063e3207fe842)

Từ đây, bây giờ có một kỹ thuật để xác định `m` từ `M`, cho biết
độ dài cạnh cho một đa giác với gấp đôi số cạnh. Bắt đầu với một
hình lục giác, Liu Hui có thể xác định chiều dài cạnh của một dodecagon bằng cách sử dụng công thức này.
Sau đó tiếp tục lặp lại để xác định chiều dài cạnh của một
24-gon cho trước chiều dài cạnh của một dodecagon. Ông có thể làm điều này đệ quy như
nhiều lần cần thiết. Biết cách xác định diện tích của các đa giác này,
Liu Hui sau đó có thể ước lượng `π`.

## Tài Liệu Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Liu_Hui%27s_%CF%80_algorithm)
