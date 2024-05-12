# Danh Sách Liên Kết

_Tìm hiểu bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, một **danh sách liên kết** là một tập hợp tuyến tính các phần tử dữ liệu, trong đó thứ tự tuyến tính không được xác định bởi vị trí vật lý trong bộ nhớ. Thay vào đó, mỗi phần tử trỏ đến phần tử tiếp theo. Đó là một cấu trúc dữ liệu bao gồm một nhóm các nút cùng đại diện cho một chuỗi. Dưới dạng đơn giản nhất, mỗi nút bao gồm dữ liệu và một tham chiếu (nói cách khác, một liên kết) đến nút tiếp theo trong chuỗi. Cấu trúc này cho phép việc chèn hoặc xóa hiệu quả các phần tử từ bất kỳ vị trí nào trong chuỗi trong quá trình lặp. Các biến thể phức tạp hơn thêm các liên kết bổ sung, cho phép việc chèn hoặc xóa hiệu quả từ các tham chiếu phần tử tùy ý. Một hạn chế của danh sách liên kết là thời gian truy cập tuyến tính (và khó xử lý). Truy cập nhanh, như truy cập ngẫu nhiên, không khả thi. Mảng có sự tương đồng bộ hơn so với danh sách liên kết.

![Linked List](./images/linked-list.jpeg)

_Tạo với [okso.app](https://okso.app)_

## Mã Giả Cho Các Hoạt Động Cơ Bản

### Chèn

```text
Thêm(giá_trị)
  Tiền: giá_trị là giá trị để thêm vào danh sách
  Sau: giá_trị đã được đặt ở cuối danh sách
  n ← nút(giá_trị)
  nếu đầu = ø
    đầu ← n
    cuối ← n
  nếu không
    cuối.kế_tiếp ← n
    cuối ← n
  kết thúc nếu
end Thêm
```

```text
ChènTrước(giá_trị)
 Tiền: giá_trị là giá trị để thêm vào danh sách
 Sau: giá_trị đã được đặt ở đầu danh sách
 n ← nút(giá_trị)
 n.kế_tiếp ← đầu
 đầu ← n
 nếu cuối = ø
   cuối ← n
 kết thúc
end ChènTrước
```

### Tìm Kiếm

```text
Chứa(đầu, giá_trị)
  Tiền: đầu là nút đầu trong danh sách
       giá_trị là giá trị để tìm kiếm
  Sau: phần tử có thể có trong danh sách liên kết, true; nếu không, là false
  n ← đầu
  khi n != ø và n.giá_trị != giá_trị
    n ← n.kế_tiếp
  kết thúc khi
  nếu n = ø
    trả về false
  kết thúc nếu
  trả về true
end Chứa
```

### Xóa

```text
Xóa(đầu, giá_trị)
  Tiền: đầu là nút đầu trong danh sách
       giá_trị là giá trị để loại bỏ khỏi danh sách
  Sau: giá_trị được loại bỏ khỏi danh sách, true; nếu không, là false
  nếu đầu = ø
    trả về false
  kết thúc nếu
  n ← đầu
  nếu n.giá_trị = giá_trị
    nếu đầu = cuối
      đầu ← ø
      cuối ← ø
    nếu không
      đầu ← đầu.kế_tiếp
    kết thúc nếu
    trả về true
  kết thúc nếu
  khi n.kế_tiếp != ø và n.kế_tiếp.giá_trị != giá_trị
    n ← n.kế_tiếp
  kết thúc khi
  nếu n.kế_tiếp != ø
    nếu n.kế_tiếp = cuối
      cuối ← n
      cuối.kế_tiếp = null
    nếu không
      n.kế_tiếp ← n.kế_tiếp.kế_tiếp
    kết thúc nếu
    trả về true
  kết thúc nếu
  trả về false
end Xóa
```

### Duyệt

```text
Duyệt(đầu)
  Tiền: đầu là nút đầu trong danh sách
  Sau: các mục trong danh sách đã được duyệt
  n ← đầu
  khi n != ø
    xuất n.giá_trị
    n ← n.kế_tiếp
  kết thúc khi
end Duyệt
```

### Duyệt Ngược

```text
DuyệtNgược(đầu, cuối)
  Tiền: đầu và cuối thuộc cùng một danh sách
  Sau: các mục trong danh sách đã được duyệt theo thứ tự ngược lại
  nếu cuối != ø
    hiện_tại ← cuối
    khi hiện_tại != đầu
      trước ← đầu
      khi trước.kế_tiếp != hiện_tại
        trước ← trước.kế_tiếp
      kết thúc khi
      xuất hiện_tại.giá_trị
      hiện_tại ← trước
    kết thúc khi
   xuất hiện_tại.giá_trị
  kết thúc nếu
end DuyệtNgược
```

## Phức Tạp

### Phức Tạp Thời Gian

| Truy Cập | Tìm Kiếm | Chèn | Xóa  |
| :------: | :------: | :--: | :--: |
|   O(n)   |   O(n)   | O(1) | O(n) |

### Phức Tạp Không Gian

O(n)

## Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Linked_list)
- [YouTube](https://www.youtube.com/watch?v=njTh_OwMljA&index=2&t=1s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
