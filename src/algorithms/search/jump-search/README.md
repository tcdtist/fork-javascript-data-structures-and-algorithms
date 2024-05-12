# Tìm Kiếm Bước Nhảy

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Giống như Tìm kiếm nhị phân, **Tìm kiếm bước nhảy** (hoặc **Tìm kiếm khối**) là một thuật toán tìm kiếm
cho các mảng đã được sắp xếp. Ý tưởng cơ bản là kiểm tra ít phần tử hơn
(so với tìm kiếm tuyến tính) bằng cách nhảy về phía trước theo các bước cố định hoặc bỏ qua một số phần tử thay vì tìm kiếm tất cả
các phần tử.

Ví dụ, giả sử chúng ta có một mảng `arr[]` có kích thước `n` và khối (để nhảy) có kích thước `m`. Sau đó, chúng ta tìm kiếm tại các chỉ số `arr[0]`, `arr[m]`, `arr[2 * m]`, ..., `arr[k * m]` và
vân vân. Khi chúng ta tìm được khoảng `arr[k * m] < x < arr[(k+1) * m]`, chúng ta thực hiện một
thao tác tìm kiếm tuyến tính từ chỉ số `k * m` để tìm phần tử `x`.

**Kích thước khối tối ưu là bao nhiêu để bỏ qua?**
Trong trường hợp xấu nhất, chúng ta phải thực hiện `n/m` bước nhảy và nếu giá trị cuối cùng đã kiểm tra lớn hơn phần tử cần tìm, chúng ta thực hiện `m - 1` so sánh nữa cho tìm kiếm tuyến tính. Do đó, tổng số so sánh trong trường hợp xấu nhất sẽ là `((n/m) + m - 1)`. Giá trị của hàm `((n/m) + m - 1)` sẽ là tối thiểu khi `m = √n`. Do đó, kích thước bước tốt nhất là `m = √n`.

## Phức Tạp

**Phức tạp thời gian**: `O(√n)` - bởi vì chúng ta tìm kiếm theo khối có kích thước `√n`.

## Tham Khảo

- [GeeksForGeeks](https://www.geeksforgeeks.org/jump-search/)
- [Wikipedia](https://en.wikipedia.org/wiki/Jump_search)
