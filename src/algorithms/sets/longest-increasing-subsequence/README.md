# Dãy con tăng dài nhất

_Đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Bài toán dãy con tăng dài nhất là tìm một dãy con của một dãy cho trước sao cho các phần tử của dãy con đó được sắp xếp theo thứ tự tăng dần, từ thấp đến cao, và dãy con đó có độ dài lớn nhất có thể. Dãy con này không nhất thiết phải là liên tục hoặc duy nhất.

## Độ phức tạp

Bài toán dãy con tăng dài nhất có thể được giải quyết trong thời gian `O(n log n)`, trong đó `n` là độ dài của dãy đầu vào.

Phương pháp lập trình động có độ phức tạp là `O(n * n)`.

## Ví dụ

Trong 16 số đầu tiên của dãy Van der Corput nhị phân

```
0, 8, 4, 12, 2, 10, 6, 14, 1, 9, 5, 13, 3, 11, 7, 15
```

một dãy con tăng dài nhất là

```
0, 2, 6, 9, 11, 15.
```

Dãy con này có độ dài là sáu;
dãy đầu vào không có dãy con tăng gồm bảy phần tử.
Dãy con tăng dài nhất trong ví dụ này không phải là duy nhất: ví dụ,

```
0, 4, 6, 9, 11, 15 hoặc
0, 2, 6, 9, 13, 15 hoặc
0, 4, 6, 9, 13, 15
```

là các dãy con tăng có cùng độ dài trong cùng một dãy đầu vào.

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Longest_increasing_subsequence)
- [Phương pháp lập trình động trên YouTube](https://www.youtube.com/watch?v=CE2b_-XfVDk&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
