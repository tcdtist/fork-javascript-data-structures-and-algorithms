# Doubly Linked List - Danh Sách Liên Kết Hai Chiều

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, **doubly linked list** là một cấu trúc dữ liệu liên kết bao gồm một tập hợp các bản ghi liên kết tuần tự gọi là các nút. Mỗi nút chứa hai trường, được gọi là liên kết, đó là các tham chiếu đến nút trước đó và nút tiếp theo trong chuỗi các nút. Các liên kết trước đó và tiếp theo của các nút đầu và cuối, tương ứng, trỏ đến một loại kết thúc, thường là một nút báo hiệu hoặc null, để dễ dàng đi qua danh sách. Nếu chỉ có một nút báo hiệu, thì danh sách được liên kết vòng qua nút báo hiệu. Nó có thể được tưởng tượng như là hai danh sách liên kết đơn được hình thành từ các mục dữ liệu giống nhau, nhưng theo thứ tự tuần tự ngược lại.

![Danh Sách Liên Kết Hai Chiều](./images/doubly-linked-list.jpeg)

_Tạo với [okso.app](https://okso.app)_

Hai liên kết nút cho phép đi qua danh sách theo cả hai hướng. Trong khi thêm hoặc xóa một nút trong danh sách liên kết hai chiều đòi hỏi thay đổi nhiều liên kết hơn so với các hoạt động tương tự trên danh sách liên kết đơn, các hoạt động này lại đơn giản hơn và tiềm năng hiệu quả hơn (đối với các nút không phải là nút đầu) vì không cần theo dõi nút trước đó trong quá trình đi qua hoặc không cần phải đi qua danh sách để tìm nút trước đó, để liên kết của nó có thể được sửa đổi.

## Mã Giả cho Các Hoạt Động Cơ Bản

### Thêm

```text
Thêm(giá_trị)
  Tiền: giá_trị là giá trị để thêm vào danh sách
  Sau: giá_trị đã được đặt ở cuối danh sách
  n ← nút(giá_trị)
  nếu đầu = ø
    đầu ← n
    cuối ← n
  ngược lại
    n.trước ← cuối
    cuối.sau ← n
    cuối ← n
  kết thúc nếu
end Thêm
```

### Xóa

```text
Xóa(đầu, giá_trị)
  Tiền: đầu là nút đầu trong danh sách
        giá_trị là giá trị để xóa khỏi danh sách
  Sau: giá_trị được xóa khỏi danh sách, true; nếu không, là false
  nếu đầu = ø
    trả về false
  kết thúc nếu
  nếu giá_trị = giá_trị_đầu
    nếu đầu = cuối
      đầu ← ø
      cuối ← ø
    ngược lại
      đầu ← đầu.sau
      đầu.trước ← ø
    kết thúc nếu
    trả về true
  kết thúc nếu
  n ← đầu.sau
  trong khi n != ø và giá_trị !== giá_trị của n
    n ← n.sau
  kết thúc trong khi
  nếu n = cuối
    cuối ← cuối.trước
    cuối.sau ← ø
    trả về true
  ngược lại nếu n != ø
    n.trước.sau ← n.sau
    n.sau.trước ← n.trước
    trả về true
  kết thúc nếu
  trả về false
end Xóa
```

### Điều Hướng Ngược

```text
ĐiềuHướngNgược(cuối)
  Tiền: cuối là nút của danh sách cần đi qua
  Sau: danh sách đã được đi qua theo thứ tự ngược lại
  n ← cuối
  trong khi n != ø
    cho nút giá_trị
    n ← n.trước
  kết thúc trong khi
end Điều Hướng Ngược
```

## Độ Phức Tạp

## Độ Phức Tạp Thời Gian

| Truy Cập | Tìm Kiếm | Thêm | Xóa  |
| :------: | :------: | :--: | :--: |
|   O(n)   |   O(n)   | O(1) | O(n) |

### Độ Phức Tạp Không Gian

O(n)

## Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Doubly_linked_list)
- [YouTube](https://www.youtube.com/watch?v=JdQeNxWCguQ&t=7s&index=72&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
