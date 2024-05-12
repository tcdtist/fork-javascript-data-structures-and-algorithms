# Thuật Toán Z

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Thuật toán Z tìm các xuất hiện của một "từ" `W` trong một "chuỗi văn bản" `T` với thời gian tuyến tính `O(|W| + |T|)`.

Cho một chuỗi `S` có độ dài `n`, thuật toán tạo ra một mảng, `Z` trong đó `Z[i]` biểu thị chuỗi con dài nhất bắt đầu từ `S[i]` mà cũng là một tiền tố của `S`. Tìm `Z` cho chuỗi thu được bằng cách nối từ `W` với một ký tự nonce, ví dụ `$` sau đó là văn bản, `T`, giúp cho việc so khớp mẫu, vì nếu có một chỉ số `i` nào đó sao cho `Z[i]` bằng độ dài mẫu, thì mẫu phải có mặt tại điểm đó.

Mặc dù mảng `Z` có thể được tính toán với hai vòng lặp lồng nhau trong thời gian `O(|W| * |T|)`, chiến lược sau đây cho thấy cách thu được nó trong thời gian tuyến tính, dựa trên ý tưởng rằng khi chúng ta lặp qua các ký tự trong chuỗi (chỉ số `i` từ `1` đến `n - 1`), chúng ta duy trì một khoảng `[L, R]` là khoảng với `R` tối đa sao cho `1 ≤ L ≤ i ≤ R` và `S[L...R]` là một tiền tố cũng là một chuỗi con (nếu không có khoảng nào tồn tại, chỉ cần đặt `L = R =  - 1`). Đối với `i = 1`, chúng ta có thể dễ dàng tính toán `L` và `R` bằng cách so sánh `S[0...]` với `S[1...]`.

**Ví dụ về mảng Z**

```
Chỉ số           0   1   2   3   4   5   6   7   8   9  10  11
Văn bản           a   a   b   c   a   a   b   x   a   a   a   z
Giá trị Z        X   1   0   0   3   1   0   0   2   2   1   0
```

Các ví dụ khác

```
chuỗi =  a a a a a a
Z[] =  x 5 4 3 2 1
```

```
chuỗi =  a a b a a c d
Z[] =  x 1 0 2 1 0 0
```

```
chuỗi =  a b a b a b a b
Z[] =  x 0 6 0 4 0 2 0
```

**Ví dụ về hộp Z**

![z-box](https://ivanyu.me/wp-content/uploads/2014/09/zalg1.png)

## Phức Tạp

- **Thời gian:** `O(|W| + |T|)`
- **Không gian:** `O(|W|)`

## Tham Khảo

- [GeeksForGeeks](https://www.geeksforgeeks.org/z-algorithm-linear-time-pattern-searching-algorithm/)
- [YouTube](https://www.youtube.com/watch?v=CpZh4eF8QBw&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=70)
- [Thuật toán Z bởi Ivan Yurchenko](https://ivanyu.me/blog/2013/10/15/z-algorithm/)
