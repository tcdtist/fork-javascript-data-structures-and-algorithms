# Cây Heap (Cấu trúc dữ liệu)

_Bạn có thể đọc bản dịch bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, một **cây heap** là một cấu trúc dữ liệu dựa trên cây đặc biệt được thiết kế để thỏa mãn thuộc tính cây heap mô tả dưới đây.

Trong một _heap tối thiểu_, nếu `P` là một nút cha của `C`, thì khóa (giá trị) của `P` phải nhỏ hơn hoặc bằng khóa của `C`.

![MinHeap](./images/min-heap.jpeg)

_Tạo với [okso.app](https://okso.app)_

Trong một _heap tối đa_, khóa của `P` phải lớn hơn hoặc bằng khóa của `C`.

![MaxHeap](./images/max-heap.jpeg)

Nút ở "đỉnh" của heap mà không có nút cha được gọi là nút gốc.

## Phức Tạp Thời Gian

Dưới đây là phức tạp thời gian của các cấu trúc dữ liệu heap khác nhau. Tên hàm giả sử một heap tối đa.

| Hoạt Động                                                                                              | tìm-max    | xóa-max    | chèn       | tăng-khóa  | hợp        |
| ------------------------------------------------------------------------------------------------------ | ---------- | ---------- | ---------- | ---------- | ---------- |
| [Nhị Phân](https://en.wikipedia.org/wiki/Binary_heap)                                                  | `Θ(1)`     | `Θ(log n)` | `O(log n)` | `O(log n)` | `Θ(n)`     |
| [Leftist](https://en.wikipedia.org/wiki/Leftist_tree)                                                  | `Θ(1)`     | `Θ(log n)` | `Θ(log n)` | `O(log n)` | `Θ(log n)` |
| [Hình thái nhị phân](https://en.wikipedia.org/wiki/Binomial_heap)                                      | `Θ(1)`     | `Θ(log n)` | `Θ(1)`     | `O(log n)` | `O(log n)` |
| [Hình thái Fibonacci](https://en.wikipedia.org/wiki/Fibonacci_heap)                                    | `Θ(1)`     | `Θ(log n)` | `Θ(1)`     | `Θ(1)`     | `Θ(1)`     |
| [Hình thái Pairing](https://en.wikipedia.org/wiki/Pairing_heap)                                        | `Θ(1)`     | `Θ(log n)` | `Θ(1)`     | `o(log n)` | `Θ(1)`     |
| [Brodal](https://en.wikipedia.org/wiki/Brodal_queue)                                                   | `Θ(1)`     | `Θ(log n)` | `Θ(1)`     | `Θ(1)`     | `Θ(1)`     |
| [Xếp hạng-Pairing](https://en.wikipedia.org/w/index.php?title=Rank-pairing_heap&action=edit&redlink=1) | `Θ(1)`     | `Θ(log n)` | `Θ(1)`     | `Θ(1)`     | `Θ(1)`     |
| [Fibonacci nghiêm ngặt](https://en.wikipedia.org/wiki/Fibonacci_heap)                                  | `Θ(1)`     | `Θ(log n)` | `Θ(1)`     | `Θ(1)`     | `Θ(1)`     |
| [2-3 heap](https://en.wikipedia.org/wiki/2%E2%80%933_heap)                                             | `O(log n)` | `O(log n)` | `O(log n)` | `Θ(1)`     | `?`        |

Trong đó:

- **tìm-max (hoặc tìm-min):** tìm một phần tử tối đa của heap tối đa hoặc một phần tử tối thiểu của heap tối thiểu, tương ứng (còn được gọi là _đỉnh_)
- **xóa-max (hoặc xóa-min):** loại bỏ nút gốc của heap tối đa (hoặc heap tối thiểu), tương ứng
- **chèn:** thêm một khóa mới vào heap (còn được gọi là _đẩy_)
- **tăng-khóa hoặc giảm-khóa:** cập nhật một khóa trong heap tối đa hoặc tối thiểu, tương ứng
- **hợp:** kết hợp hai heap để tạo ra một heap mới hợp lệ chứa tất cả các phần tử của cả hai, phá hủy các heap gốc.

> Trong kho lưu trữ này, [MaxHeap.js](./MaxHeap.js) và [MinHeap.js](./MinHeap.js) là các ví dụ về heap **Nhị phân**.

## Cài Đặt

- [MaxHeap.js](./MaxHeap.js) và [MinHeap.js](./MinHeap.js)
- [MaxHeapAdhoc.js](./MaxHeapAdhoc.js) và [MinHeapAdhoc.js](./MinHeapAdhoc.js) - Phiên bản tối giản (tùy ý) của cấu trúc dữ liệu MinHeap/MaxHeap không có các phụ thuộc bên ngoài và dễ dàng sao chép và sử dụng trong quá trình phỏng vấn lập trình nếu được phép bởi người phỏng vấn (vì nhiều cấu trúc dữ liệu trong JS thiếu).

## Tham Khảo

- [Wikipedia](<https://en.wikipedia.org/wiki/Heap_(data_structure)>)
- [YouTube](https://www.youtube.com/watch?v=t0Cq6tVNRBA&index=5&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
