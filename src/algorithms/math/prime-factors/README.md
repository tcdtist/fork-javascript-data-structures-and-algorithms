# Các Thừa số Nguyên tố

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Số nguyên tố** là một số tự nhiên lớn hơn `1` mà **không thể** được tạo ra bằng cách nhân với các số tự nhiên khác. Một số nguyên tố đầu tiên là: `2`, `3`, `5`, `7`, `11`, `13`, `17`, `19` và cứ tiếp tục như vậy.

Nếu chúng ta **có thể** tạo ra nó bằng cách nhân với các số tự nhiên khác thì đó là một **Số Hợp**.

![Các số hợp](https://www.mathsisfun.com/numbers/images/prime-composite.svg)

_Nguồn hình ảnh: [Math is Fun](https://www.mathsisfun.com/prime-factorization.html)_

**Các thừa số nguyên tố** là những [số nguyên tố](https://en.wikipedia.org/wiki/Prime_number) mà khi nhân lại với nhau sẽ cho ra số gốc. Ví dụ `39` sẽ có các thừa số nguyên tố là `3` và `13` đều là số nguyên tố. Một ví dụ khác là `15` có các thừa số nguyên tố là `3` và `5`.

![Thừa số](https://www.mathsisfun.com/numbers/images/factor-2x3.svg)

_Nguồn hình ảnh: [Math is Fun](https://www.mathsisfun.com/prime-factorization.html)_

## Tìm các thừa số nguyên tố và số lượng chính xác của chúng

Phương pháp là tiếp tục chia số tự nhiên `n` cho các chỉ số từ `i = 2` đến `i = n` (chỉ số nguyên tố). Giá trị của `n` sẽ bị ghi đè bởi `(n / i)` trong mỗi lần lặp.

Độ phức tạp thời gian cho đến bây giờ là `O(n)` trong trường hợp xấu nhất vì vòng lặp chạy từ chỉ số `i = 2` đến `i = n`. Độ phức tạp thời gian này có thể được giảm từ `O(n)` xuống `O(sqrt(n))`. Sự tối ưu hóa được đạt được khi vòng lặp chạy từ `i = 2` đến `i = sqrt(n)`. Bây giờ, chúng ta chỉ cần đi đến `O(sqrt(n))` vì khi `i` trở nên lớn hơn `sqrt(n)`, chúng ta đã xác nhận rằng không có chỉ số `i` nào còn lại có thể chia `n` hoàn toàn ngoại trừ `n` chính nó.

## Công thức Hardy-Ramanujan để tính xấp xỉ số lượng thừa số nguyên tố

Năm 1917, G.H Hardy và Srinivasa Ramanujan đã sáng tạo ra một định lý khẳng định rằng số thứ tự bình thường của số `ω(n)` của các thừa số nguyên tố phân biệt của một số `n` là `log(log(n))`.

Nói một cách ngắn gọn, điều này có nghĩa là hầu hết các số có khoảng cách giữa chúng là số lượng thừa số nguyên tố phân biệt này.

## Tham khảo

- [Các số nguyên tố trên Math is Fun](https://www.mathsisfun.com/prime-factorization.html)
- [Các số nguyên tố trên Wikipedia](https://en.wikipedia.org/wiki/Prime_number)
- [Định lý Hardy-Ramanujan trên Wikipedia](https://en.wikipedia.org/wiki/Hardy%E2%80%93Ramanujan_theorem)
- [Phân tích thừa số nguyên tố của một số trên Youtube](https://www.youtube.com/watch?v=6PDtgHhpCHo&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=82)
