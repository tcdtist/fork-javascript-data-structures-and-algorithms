# Thuật toán Mật mã Caesar

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong mật mã học, **Mật mã Caesar**, còn được gọi là **mã của Caesar**, **mật mã dịch chuyển**, **mã Caesar** hoặc **dịch chuyển Caesar**, là một trong những kỹ thuật mã hóa đơn giản và được biết đến rộng rãi nhất. Đây là một dạng của mật mã thay thế, trong đó mỗi chữ cái trong văn bản gốc được thay thế bởi một chữ cái cách đó một số vị trí nhất định trong bảng chữ cái. Ví dụ, với một dịch chuyển sang trái `3`, `D` sẽ được thay thế bởi `A`, `E` sẽ trở thành `B`, v.v. Phương pháp này được đặt theo tên Julius Caesar, người đã sử dụng nó trong thư từ cá nhân của mình.

![Thuật toán Mật mã Caesar](https://upload.wikimedia.org/wikipedia/commons/4/4a/Caesar_cipher_left_shift_of_3.svg)

## Ví dụ

Sự biến đổi này có thể được thể hiện bằng cách căn chỉnh hai bảng chữ cái; bảng chữ cái mã là bảng chữ cái gốc xoay trái hoặc phải một số vị trí nhất định. Ví dụ, đây là một mật mã Caesar sử dụng một xoay trái ba vị trí, tương đương với một dịch chuyển phải 23 (tham số dịch chuyển được sử dụng như là khóa):

```text
Bảng chữ cái gốc:  ABCDEFGHIJKLMNOPQRSTUVWXYZ
Bảng chữ cái mã:   XYZABCDEFGHIJKLMNOPQRSTUVW
```

Khi mã hóa, người ta tìm từng chữ cái của tin nhắn trong dòng "bảng chữ cái gốc" và viết ra chữ cái tương ứng trong dòng "bảng chữ cái mã".

```text
Văn bản gốc:  THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG
Văn bản mã:   QEB NRFZH YOLTK CLU GRJMP LSBO QEB IXWV ALD
```

## Độ phức tạp

- Thời gian: `O(|n|)`
- Không gian: `O(|n|)`

## Tài liệu tham khảo

- [Mật mã Caesar trên Wikipedia](https://en.wikipedia.org/wiki/Caesar_cipher)
