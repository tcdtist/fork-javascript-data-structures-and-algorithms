# Sắp xếp Radix

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, **sắp xếp radix** là một thuật toán sắp xếp số nguyên không so sánh
sắp xếp dữ liệu với các khóa số nguyên bằng cách nhóm các khóa theo từng chữ số
chung vị trí và giá trị quan trọng. Cần có một ký hiệu vị trí,
nhưng vì số nguyên có thể đại diện cho chuỗi ký tự
(ví dụ, tên hoặc ngày) và số thực được định dạng đặc biệt,
sắp xếp radix không giới hạn ở số nguyên.

_Tên này đến từ đâu?_

Trong hệ thống số toán học, _radix_ hoặc cơ số là số lượng chữ số duy nhất,
bao gồm số không, được sử dụng để đại diện cho các số trong hệ thống số có vị trí.
Ví dụ, hệ thống nhị phân (sử dụng số 0 và 1) có một radix là 2 và hệ thống thập phân
(sử dụng số 0 đến 9) có một radix là 10.

## Hiệu suất

Chủ đề về hiệu suất của sắp xếp radix so với các thuật toán sắp xếp khác là
một chút phức tạp và phụ thuộc vào nhiều hiểu biết sai lầm. Dù sắp xếp radix
có hiệu suất bằng nhau, kém hiệu suất hoặc cao hơn so với các thuật toán
so sánh tốt nhất phụ thuộc vào chi tiết của các giả định được thực hiện.
Phức tạp của sắp xếp radix là `O(wn)` cho `n` khóa là số nguyên của kích thước từ `w`.
Đôi khi `w` được hiển thị như một hằng số, điều này sẽ làm cho sắp xếp radix tốt hơn
(đối với `n` đủ lớn) so với các thuật toán sắp xếp so sánh tốt nhất,
tất cả đều thực hiện `O(n log n)` so sánh để sắp xếp `n` khóa. Tuy nhiên, trong
tổng quát `w` không thể được xem xét là một hằng số: nếu tất cả các `n` khóa là phân biệt,
thì `w` phải ít nhất là `log n` cho máy truy cập ngẫu nhiên có thể
lưu trữ chúng trong bộ nhớ, điều này cho tối đa là một phức tạp thời gian `O(n log n)`.
Điều này dường như làm cho sắp xếp radix tối đa là tương đương hiệu quả như các
sắp xếp dựa trên so sánh tốt nhất (và tồi hơn nếu khóa dài hơn nhiều so với `log n`).

![Sắp xếp Radix](./images/radix-sort.png)

## Phức tạp

| Tên               | Tốt nhất | Trung bình | Tệ nhất | Bộ nhớ | Ổn định | Bình luận                       |
| ----------------- | :------: | :--------: | :-----: | :----: | :-----: | :------------------------------ |
| **Sắp xếp radix** |  n \* k  |   n \* k   | n \* k  | n + k  |   Có    | k - chiều dài của khóa dài nhất |

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Radix_sort)
- [YouTube](https://www.youtube.com/watch?v=XiuSW_mEn7g&index=62&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [ResearchGate](https://www.researchgate.net/figure/Simplistic-illustration-of-the-steps-performed-in-a-radix-sort-In-this-example-the_fig1_291086231)
