# Sắp xếp đếm - Counting Sort

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, **sắp xếp đếm** là một thuật toán để sắp xếp một tập hợp các đối tượng theo các khóa là số nguyên nhỏ; tức là, đó là một thuật toán sắp xếp số nguyên. Thuật toán này hoạt động bằng cách đếm số lượng đối tượng có cùng giá trị khóa riêng biệt, và sử dụng các phép toán số học trên các số lượng đó để xác định vị trí của mỗi giá trị khóa trong chuỗi kết quả. Thời gian chạy của nó là tuyến tính theo số lượng phần tử và sự khác biệt giữa giá trị khóa lớn nhất và nhỏ nhất, vì vậy nó chỉ thích hợp cho việc sử dụng trực tiếp trong các tình huống mà sự biến động về khóa không đáng kể hơn số lượng phần tử. Tuy nhiên, nó thường được sử dụng như một phụ thuộc trong một thuật toán sắp xếp khác, radix sort, có thể xử lý các khóa lớn hơn một cách hiệu quả hơn.

Bởi vì sắp xếp đếm sử dụng các giá trị khóa như là chỉ số vào một mảng, nó không phải là một sắp xếp so sánh, và giới hạn dưới `Ω(n log n)` cho sắp xếp so sánh không áp dụng cho nó. Bucket sort có thể được sử dụng cho nhiều công việc tương tự như sắp xếp đếm, với một phân tích thời gian tương tự; tuy nhiên, so với sắp xếp đếm, bucket sort yêu cầu các danh sách liên kết, mảng động hoặc một lượng lớn bộ nhớ được cấp phát trước để giữ các tập hợp các phần tử trong mỗi thùng, trong khi sắp xếp đếm thay vào đó lưu trữ một con số duy nhất (số lượng phần tử) mỗi thùng.

Sắp xếp đếm hoạt động tốt nhất khi phạm vi số cho mỗi phần tử mảng rất nhỏ.

## Thuật toán

**Bước I**

Trong bước đầu tiên, chúng tôi tính toán số lượng tất cả các phần tử của mảng đầu vào `A`. Sau đó, lưu kết quả vào mảng đếm `C`. Cách chúng tôi đếm được mô tả như sau.

![Sắp xếp đếm](https://3.bp.blogspot.com/-jJchly1BkTc/WLGqCFDdvCI/AAAAAAAAAHA/luljAlz2ptMndIZNH0KLTTuQMNsfzDeFQCLcB/s1600/CSortUpdatedStepI.gif)

**Bước II**

Trong bước thứ hai, chúng tôi tính toán có bao nhiêu phần tử tồn tại trong mảng đầu vào `A` mà nhỏ hơn hoặc bằng chỉ số cho trước. `Ci` = số lượng phần tử nhỏ hơn hoặc bằng `i` trong mảng đầu vào.

![Sắp xếp đếm](https://1.bp.blogspot.com/-1vFu-VIRa9Y/WLHGuZkdF3I/AAAAAAAAAHs/8jKu2dbQee4ap9xlVcNsILrclqw0UxAVACLcB/s1600/Step-II.png)

**Bước III**

Trong bước này, chúng tôi đặt phần tử mảng đầu vào `A` vào vị trí đã sắp xếp bằng cách sử dụng mảng đếm đã xây dựng trong bước hai. Chúng tôi sử dụng mảng kết quả `B` để lưu trữ các phần tử đã sắp xếp. Ở đây, chúng tôi xử lý chỉ số của `B` bắt đầu từ số không.

![Sắp xếp đếm](https://1.bp.blogspot.com/-xPqylngqASY/WLGq3p9n9vI/AAAAAAAAAHM/JHdtXAkJY8wYzDMBXxqarjmhpPhM0u8MACLcB/s1600/ResultArrayCS.gif)

## Phức tạp

| Tên             | Tốt nhất | Trung bình | Tệ nhất | Bộ nhớ | Ổn định | Bình luận                  |
| --------------- | :------: | :--------: | :-----: | :----: | :-----: | :------------------------- |
| **Sắp xếp đếm** |  n + r   |   n + r    |  n + r  | n + r  |   Có    | r - số lớn nhất trong mảng |

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Counting_sort)
- [YouTube](https://www.youtube.com/watch?v=OKd534EWcdk&index=61&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [EfficientAlgorithms](https://efficientalgorithms.blogspot.com/2016/09/lenear-sorting-counting-sort.html)
