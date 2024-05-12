# Bộ nhớ cache Least Recently Used (LRU)

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Bộ nhớ cache Least Recently Used (LRU) sắp xếp các mục theo thứ tự sử dụng, cho phép bạn nhanh chóng xác định mục nào chưa được sử dụng trong thời gian dài nhất.

Hãy tưởng tượng một cái gác áo, nơi quần áo luôn được treo ở một bên. Để tìm mục ít được sử dụng nhất, hãy nhìn vào mục ở đầu kia của gác áo.

## Tuyên bố vấn đề

Thực hiện lớp LRUCache:

- `LRUCache(int capacity)` Khởi tạo bộ nhớ cache LRU với kích thước dương `capacity`.
- `int get(int key)` Trả về giá trị của `key` nếu `key` tồn tại, nếu không trả về `undefined`.
- `void set(int key, int value)` Cập nhật giá trị của `key` nếu `key` tồn tại. Nếu không, thêm cặp `key-value` vào bộ nhớ cache. Nếu số lượng key vượt quá `capacity` từ hoạt động này, **loại bỏ** key ít được sử dụng nhất.

Các hàm `get()` và `set()` phải chạy trong thời gian trung bình `O(1)`.

## Thực hiện

### Phiên bản 1: Danh sách liên kết hai chiều + Bản đồ băm

Xem ví dụ cài đặt `LRUCache` trong tệp [LRUCache.js](./LRUCache.js). Giải pháp sử dụng `HashMap` để truy cập nhanh chóng các mục cache với `O(1)` (trong trường hợp trung bình), và `DoublyLinkedList` để thúc đẩy và loại bỏ mục cache nhanh chóng với `O(1)` (trong trường hợp trung bình) (để giữ cho dung lượng bộ nhớ cache tối đa được phép).

![Danh sách liên kết](./images/lru-cache.jpg)

_Tạo với [okso.app](https://okso.app)_

Bạn cũng có thể tìm thấy nhiều ví dụ về trường hợp thử nghiệm về cách bộ nhớ cache LRU hoạt động trong tệp [LRUCache.test.js](./__test__/LRUCache.test.js).

### Phiên bản 2: Bản đồ có thứ tự

Cài đặt đầu tiên sử dụng danh sách liên kết hai chiều là tốt cho mục đích học và để hiểu rõ hơn về cách độ phức tạp thời gian trung bình `O(1)` có thể đạt được trong khi thực hiện `set()` và `get()`.

Tuy nhiên, phương pháp đơn giản hơn có thể là sử dụng một đối tượng [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) JavaScript. Đối tượng `Map` giữ các cặp khóa-giá trị và **nhớ thứ tự chèn ban đầu** của các khóa. Chúng ta có thể sử dụng sự thật này để giữ các mục đã sử dụng gần đây ở "cuối" của bản đồ bằng cách loại bỏ và thêm lại các mục. Mục ở đầu của `Map` sẽ là mục đầu tiên bị loại bỏ nếu dung lượng bộ nhớ cache vượt quá. Thứ tự của các mục có thể được kiểm tra bằng cách sử dụng `IterableIterator` như `map.keys()`.

Xem ví dụ cài đặt `LRUCacheOnMap` trong tệp [LRUCacheOnMap.js](./LRUCacheOnMap.js).

Bạn cũng có thể tìm thấy nhiều ví dụ về trường hợp thử nghiệm về cách bộ nhớ cache LRU hoạt động trong tệp [LRUCacheOnMap.test.js](./__test__/LRUCacheOnMap.test.js).

## Độ phức tạp

|            | Trung bình |
| ---------- | ---------- |
| Dung lượng | `O(n)`     |
| Lấy mục    | `O(1)`     |
| Đặt mục    | `O(1)`     |

## Tham khảo

- [Bộ nhớ cache LRU trên LeetCode](https://leetcode.com/problems/lru-cache/solutions/244744/lru-cache/)
- [Bộ nhớ cache LRU trên InterviewCake](https://www.interviewcake.com/concept/java/lru-cache)
- [Bộ nhớ cache LRU trên Wiki](https://en.wikipedia.org/wiki/Cache_replacement_policies)
