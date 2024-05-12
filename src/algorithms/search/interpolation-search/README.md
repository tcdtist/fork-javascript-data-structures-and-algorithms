# Tìm kiếm nội suy

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Tìm kiếm nội suy** là một thuật toán để tìm kiếm một khóa trong một mảng đã được sắp xếp theo các giá trị số được gán cho các khóa (giá trị khóa).

Ví dụ, chúng ta có một mảng đã được sắp xếp của `n` giá trị phân phối đều `arr[]`, và chúng ta cần viết một hàm để tìm kiếm một phần tử cụ thể `x` trong mảng đó.

**Tìm kiếm tuyến tính** tìm phần tử trong thời gian `O(n)`, **Tìm kiếm nhảy** mất thời gian `O(√ n)` và **Tìm kiếm nhị phân** mất thời gian `O(Log n)`.

**Tìm kiếm nội suy** là một cải tiến so với Tìm kiếm nhị phân trong các trường hợp, nơi các giá trị trong một mảng đã được sắp xếp _đều nhau_. Tìm kiếm nhị phân luôn đi đến phần tử giữa để kiểm tra. Ngược lại, tìm kiếm nội suy có thể đi đến các vị trí khác nhau tùy theo giá trị của khóa đang được tìm kiếm. Ví dụ, nếu giá trị của khóa gần với phần tử cuối cùng, tìm kiếm nội suy có thể bắt đầu tìm kiếm về phía cuối.

Để tìm vị trí cần tìm kiếm, nó sử dụng công thức sau:

```
// Ý tưởng của công thức là trả về giá trị cao hơn của pos
// khi phần tử cần tìm kiếm gần với arr[hi]. Và
// giá trị nhỏ hơn khi gần với arr[lo]
pos = lo + ((x - arr[lo]) * (hi - lo) / (arr[hi] - arr[Lo]))

arr[] - Mảng chứa các phần tử cần tìm kiếm
x - Phần tử cần tìm kiếm
lo - Chỉ số bắt đầu trong arr[]
hi - Chỉ số kết thúc trong arr[]
```

## Phức tạp

**Phức tạp thời gian**: `O(log(log(n))`

## Tham khảo

- [GeeksForGeeks](https://www.geeksforgeeks.org/interpolation-search/)
- [Wikipedia](https://en.wikipedia.org/wiki/Interpolation_search)
