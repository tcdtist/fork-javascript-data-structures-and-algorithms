# Cây Đoạn

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, một **cây đoạn** còn được gọi là cây thống kê là một cấu trúc dữ liệu cây được sử dụng để lưu trữ thông tin về các đoạn hoặc khoảng. Nó cho phép truy vấn xem đoạn được lưu trữ nào chứa một điểm cụ thể. Nó, về cơ bản, là một cấu trúc tĩnh; có nghĩa là, đó là một cấu trúc không thể được sửa đổi sau khi được xây dựng. Một cấu trúc dữ liệu tương tự là cây khoảng.

Một cây đoạn là một cây nhị phân. Gốc của cây đại diện cho toàn bộ mảng. Hai con của gốc đại diện cho nửa đầu tiên và nửa thứ hai của mảng. Tương tự, các con của mỗi nút tương ứng với hai nửa của mảng tương ứng với nút đó.

Chúng ta xây dựng cây từ dưới lên, với giá trị của mỗi nút là "tối thiểu" (hoặc bất kỳ hàm khác) của giá trị của các con của nó. Điều này sẽ mất thời gian `O(n log n)`. Số lượng thao tác được thực hiện là chiều cao của cây, là `O(log n)`. Để thực hiện truy vấn phạm vi, mỗi nút chia truy vấn thành hai phần, một phần con cho mỗi con. Nếu một truy vấn chứa toàn bộ mảng con của một nút, chúng ta có thể sử dụng giá trị được tính toán trước ở nút. Sử dụng tối ưu hóa này, chúng ta có thể chứng minh rằng chỉ có `O(log n)` thao tác tối thiểu được thực hiện.

## Ứng dụng

Một cây đoạn là một cấu trúc dữ liệu được thiết kế để thực hiện một số phép toán mảng cụ thể một cách hiệu quả - đặc biệt là những phép toán liên quan đến truy vấn phạm vi.

Các ứng dụng của cây đoạn nằm trong các lĩnh vực của hình học tính toán và hệ thống thông tin địa lý.

Hiện tại, cài đặt của Cây Đoạn ngụ ý rằng bạn có thể truyền bất kỳ hàm nhị phân nào (với hai tham số đầu vào) vào và do đó bạn có thể thực hiện truy vấn phạm vi cho nhiều loại hàm khác nhau. Trong các bài kiểm tra, bạn có thể tìm thấy ví dụ về việc thực hiện truy vấn phạm vi `min`, `max` và `sum` trên Cây Đoạn.

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Segment_tree)
- [YouTube](https://www.youtube.com/watch?v=ZBHKZF5w4YU&index=65&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [GeeksForGeeks](https://www.geeksforgeeks.org/segment-tree-set-1-sum-of-given-range/)
