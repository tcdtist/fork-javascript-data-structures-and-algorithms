# Mật mã Hàng rào Zigzag

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Mật mã hàng rào Zigzag** (còn gọi là **mật mã zigzag**) là một [mật mã hoán vị](https://en.wikipedia.org/wiki/Transposition_cipher) trong đó thông điệp được phân tách trên một tập hợp các hàng rào để mã hóa. Hàng rào được lấp đầy bằng các ký tự của thông điệp, bắt đầu từ góc trên bên trái và thêm một ký tự vào mỗi vị trí, di chuyển chéo xuống dưới. Khi đến hàng cuối cùng, hướng di chuyển sẽ chuyển thành chéo lên trên đến hàng đầu tiên theo một chuyển động zig-zag. Lặp lại quá trình này cho đến khi thông điệp được phân bổ hoàn toàn trên hàng rào. Thông điệp được mã hóa là kết quả của việc nối liền văn bản trên mỗi hàng rào, từ trên xuống dưới.

Từ [wikipedia](https://en.wikipedia.org/wiki/Rail_fence_cipher), đây là cách thông điệp `WE ARE DISCOVERED. FLEE AT ONCE` trông như thế nào trên hàng rào `3`-rail:

```
W . . . E . . . C . . . R . . . L . . . T . . . E
. E . R . D . S . O . E . E . F . E . A . O . C .
. . A . . . I . . . V . . . D . . . E . . . N . .
-------------------------------------------------
             WECRLTEERDSOEEFEAOCAIVDEN
```

Thông điệp sau đó có thể được giải mã bằng cách tạo lại hàng rào đã mã hóa, với cùng một mô hình di chuyển, ngoại trừ việc các ký tự chỉ được thêm vào một hàng rào mỗi lần. Để minh họa điều đó, dấu gạch ngang có thể được thêm vào các hàng rào chưa được lấp đầy. Đây là cách hàng rào trông sau khi lấp đầy hàng đầu tiên, các dấu gạch ngang đại diện cho các vị trí đã được thăm nhưng chưa được lấp đầy.

```
W . . . E . . . C . . . R . . . L . . . T . . . E
. - . - . - . - . - . - . - . - . - . - . - . - .
. . - . . . - . . . - . . . - . . . - . . . - . .
```

Đã đến lúc bắt đầu lấp đầy hàng rào tiếp theo khi số vị trí hàng rào đã thăm bằng với số lượng ký tự trong thông điệp.

## Tài liệu tham khảo

- [Mật mã Hàng rào Zigzag trên Wikipedia](https://en.wikipedia.org/wiki/Rail_fence_cipher)
- [Máy tính Mật mã Hàng rào Zigzag](https://crypto.interactive-maths.com/rail-fence-cipher.html)
