# Bloom Filter - Bộ lọc Bloom

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Bộ lọc Bloom** là một cấu trúc dữ liệu xác suất hiệu quả về không gian, được thiết kế để kiểm tra xem một phần tử có tồn tại trong một tập hợp hay không. Nó được thiết kế để hoạt động với tốc độ nhanh chóng và sử dụng bộ nhớ tối thiểu với chi phí có thể là các dương tính giả. Các dương tính giả có thể xảy ra, nhưng các âm tính giả không thể - nói cách khác, một truy vấn sẽ trả về một trong hai kết quả "có thể có trong tập hợp" hoặc "chắc chắn không trong tập hợp".

Bloom đề xuất phương pháp này cho các ứng dụng mà lượng dữ liệu nguồn sẽ đòi hỏi một lượng bộ nhớ không thể áp dụng được nếu các kỹ thuật băm không lỗi được áp dụng.

## Mô tả thuật toán

Một bộ lọc Bloom trống là một mảng bit có `m` bit, tất cả đều được đặt thành `0`. Cũng cần phải xác định `k` hàm băm khác nhau, mỗi hàm băm sẽ ánh xạ hoặc băm một phần tử của tập hợp sang một trong `m` vị trí mảng, tạo ra một phân phối ngẫu nhiên đồng đều. Thông thường, `k` là một hằng số, nhỏ hơn rất nhiều so với `m`, tỷ lệ này tương tự với số phần tử được thêm vào; việc chọn chính xác của `k` và hằng số tỷ lệ của `m` được xác định bởi tỷ lệ dương tính giả mong muốn của bộ lọc.

Dưới đây là một ví dụ về bộ lọc Bloom, đại diện cho tập hợp `{x, y, z}`. Các mũi tên màu chỉ ra các vị trí trong mảng bit mà mỗi phần tử của tập hợp được ánh xạ đến. Phần tử `w` không thuộc tập hợp `{x, y, z}`, vì nó băm tới một vị trí mảng bit chứa `0`. Đối với hình này, `m = 18` và `k = 3`.

![Bộ lọc Bloom](https://upload.wikimedia.org/wikipedia/commons/a/ac/Bloom_filter.svg)

## Các hoạt động

Có hai hoạt động chính mà một bộ lọc Bloom có thể thực hiện: _chèn_ và _tìm kiếm_. Tìm kiếm có thể dẫn đến các dương tính giả. Không thể xóa.

Nói cách khác, bộ lọc có thể nhận vào các mục. Khi chúng ta kiểm tra xem một mục đã được chèn trước đó hay chưa, nó có thể cho chúng ta biết "không" hoặc "có thể".

Cả hai hoạt động chèn và tìm kiếm đều là các hoạt động `O(1)`.

## Tạo bộ lọc

Một bộ lọc Bloom được tạo bằng cách phân bổ một kích thước nhất định. Trong ví dụ của chúng tôi, chúng tôi sử dụng `100` làm chiều dài mặc định. Tất cả các vị trí được khởi tạo thành `false`.

### Chèn

Trong quá trình chèn, một số lượng hàm băm, trong trường hợp của chúng tôi là `3` hàm băm, được sử dụng để tạo các băm của đầu vào. Các hàm băm này xuất các chỉ mục. Tại mỗi chỉ mục nhận được, chúng ta đơn giản thay đổi giá trị trong bộ lọc Bloom của chúng ta thành `true`.

### Tìm kiếm

Trong một tìm kiếm, các hàm băm giống nhau được gọi và được sử dụng để băm đầu vào. Sau đó, chúng ta kiểm tra xem các chỉ mục nhận được _tất cả_ có một giá trị `true` bên trong bộ lọc Bloom của chúng ta không. Nếu _tất cả_ đều có giá trị `true`, chúng ta biết rằng bộ lọc Bloom có thể đã có giá trị được chèn trước đó.

Tuy nhiên, không chắc chắn, vì có thể các giá trị khác được chèn trước đó đã làm cho các giá trị thành `true`. Các giá trị không nhất thiết là `true` do mục đang được tìm kiếm. Sự chắc chắn tuyệt đối là không thể trừ khi chỉ một mục đã được chèn trước đó.

Trong khi kiểm tra bộ lọc Bloom cho các chỉ mục được trả về bởi các hàm băm của chúng ta, nếu ngay cả một trong số chúng có giá trị `false`, chúng ta chắc chắn biết rằng mục đó không được chèn trước đó.

## Dương tính giả

Xác suất của các dương tính giả được xác định bởi ba yếu tố: kích thước của bộ lọc Bloom, số lượng hàm băm mà chúng ta sử dụng và số lượng các mục đã được chèn vào bộ lọc.

Công thức để tính xác suất của dương tính giả là:

( 1 - e <sup>-kn/m</sup> ) <sup>k</sup>

`k` = số lượng hàm băm

`m` = kích thước của bộ lọc

`n` = số lượng các mục đã chèn

Các biến này, `k`, `m`, và `n`, nên được chọn dựa trên mức độ chấp nhận của dương tính giả. Nếu các giá trị được chọn và xác suất kết quả quá cao, các giá trị nên được điều chỉnh và xác suất được tính toán lại.

## Ứng dụng

Một bộ lọc Bloom có thể được sử dụng trên một trang web blog. Nếu mục tiêu là chỉ hiển thị bài viết cho người đọc mà họ chưa bao giờ thấy trước đó, một bộ lọc Bloom là lựa chọn hoàn hảo. Nó có thể lưu trữ các giá trị băm dựa trên các bài viết. Sau khi một người dùng đọc một vài bài viết, chúng có thể được chèn vào bộ lọc. Lần sau khi người dùng truy cập trang web, những bài viết đó có thể được lọc ra khỏi kết quả.

Một số bài viết sẽ tất nhiên bị lọc ra một cách nhầm lẫn, nhưng chi phí là chấp nhận được. Không sao nếu một người dùng không bao giờ xem một số bài viết miễn là họ có những bài viết mới hoàn toàn khác mỗi lần họ truy cập trang web.

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Bloom_filter)
- [Bộ Lọc Bloom qua Ví Dụ](http://llimllib.github.io/bloomfilter-tutorial/)
- [Tính Xác Suất Dương Tính Giả](https://hur.st/bloomfilter/?n=4&p=&m=18&k=3)
- [Bộ Lọc Bloom trên Medium](https://blog.medium.com/what-are-bloom-filters-1ec2a50c68ff)
- [Bộ Lọc Bloom trên YouTube](https://www.youtube.com/watch?v=bEmBh1HtYrw)
