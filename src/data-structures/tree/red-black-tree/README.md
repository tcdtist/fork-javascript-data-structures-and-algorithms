# Cây Đỏ-Đen

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Cây đỏ-đen** là một loại cây tìm kiếm nhị phân cân bằng tự động trong khoa học máy tính. Mỗi nút của cây nhị phân có một bit bổ sung, và bit này thường được hiểu là màu (đỏ hoặc đen) của nút. Các bit màu này được sử dụng để đảm bảo rằng cây vẫn cân bằng một cách xấp xỉ trong quá trình chèn và xóa.

Sự cân bằng được bảo tồn bằng cách sơn mỗi nút của cây bằng một trong hai màu một cách thỏa mãn các thuộc tính nhất định, những thuộc tính này hạn chế tỉ lệ mất cân bằng của cây trong trường hợp xấu nhất. Khi cây bị thay đổi, cây mới sau đó được sắp xếp lại và sơn lại để khôi phục các thuộc tính về màu sắc. Các thuộc tính được thiết kế sao cho việc sắp xếp lại và sơn lại này có thể được thực hiện một cách hiệu quả.

Việc cân bằng của cây không hoàn hảo, nhưng đủ tốt để cho phép nó đảm bảo tìm kiếm trong thời gian `O(log n)`, trong đó `n` là tổng số phần tử trong cây. Các thao tác chèn và xóa, cùng với việc sắp xếp lại và sơn lại cây, cũng được thực hiện trong thời gian `O(log n)`.

Một ví dụ về cây đỏ-đen:

![red-black tree](https://upload.wikimedia.org/wikipedia/commons/6/66/Red-black_tree_example.svg)

## Thuộc tính

Ngoài các yêu cầu được đặt ra cho một cây tìm kiếm nhị phân, các yêu cầu sau phải được đáp ứng bởi một cây đỏ-đen:

- Mỗi nút có màu đỏ hoặc đen.
- Gốc của cây là màu đen. Quy tắc này đôi khi được bỏ qua. Vì gốc luôn có thể được thay đổi từ màu đỏ thành màu đen, nhưng không nhất thiết phải ngược lại, quy tắc này không ảnh hưởng nhiều đến phân tích.
- Tất cả các lá (NIL) đều là màu đen.
- Nếu một nút có màu đỏ, thì cả hai con của nó đều là màu đen.
- Mọi đường từ một nút cụ thể đến bất kỳ nút lá con NIL nào của nó đều chứa cùng số lượng nút đen.

Một số định nghĩa: số lượng nút đen từ gốc đến một nút là **độ sâu đen** của nút đó; số lượng đều nhau của các nút đen trên tất cả các đường từ gốc đến các lá được gọi là **chiều cao đen** của cây đỏ-đen.

Những ràng buộc này áp dụng một tính chất quan trọng của cây đỏ-đen: _đường từ gốc đến lá xa nhất không dài hơn gấp đôi đường từ gốc đến lá gần nhất_. Kết quả là cây xấp xỉ cân bằng chiều cao. Vì các thao tác như chèn, xóa và tìm kiếm giá trị đều yêu cầu thời gian tối đa tỉ lệ thuận với chiều cao của cây, giới hạn trên lý thuyết này về chiều cao cho phép cây đỏ-đen là hiệu quả trong trường hợp xấu nhất, khác với cây tìm kiếm nhị phân thông thường.

## Cân bằng trong quá trình chèn

### Nếu cậu là MÀU ĐỎ

![Cân bằng cây Đỏ-Đen](https://www.geeksforgeeks.org/wp-content/uploads/redBlackCase2.png)

### Nếu cậu là MÀU ĐEN

- Trường hợp Trái Trái (`p` là con trái của `g` và `x` là con trái của `p`)
- Trường hợp Trái Phải (`p` là con trái của `g` và `x` là con phải của `p`)
- Trường hợp Phải Phải (`p` là con phải của `g` và `x` là con phải của `p`)
- Trường hợp Phải Trái (`p` là con phải của `g` và `x` là con trái của `p`)

#### Trường hợp Trái Trái (Xem g, p và x)

![Cân bằng cây Đỏ-Đen](https://www.geeksforgeeks.org/wp-content/uploads/redBlackCase3a1.png)

#### Trường hợp Trái Phải (Xem g, p và x)

![Cân bằng cây Đỏ-Đen](https://www.geeksforgeeks.org/wp-content/uploads/redBlackCase3b.png)

#### Trường hợp Phải Phải (Xem g, p và x)

![Cân bằng cây Đỏ-Đen](https://www.geeksforgeeks.org/wp-content/uploads/redBlackCase3c.png)

#### Trường hợp Phải Trái (Xem g, p và x)

![Cân bằng cây Đỏ-Đen](https://www.geeksforgeeks.org/wp-content/uploads/redBlackCase3d.png)

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree)
- [Chèn Cây Đỏ-Đen bởi Tushar Roy (YouTube)](https://www.youtube.com/watch?v=UaLIHuR1t8Q&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=63)
- [Xóa Cây Đỏ-Đen bởi Tushar Roy (YouTube)](https://www.youtube.com/watch?v=CTvfzU_uNKE&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=64)
- [Chèn Cây Đỏ-Đen trên GeeksForGeeks](https://www.geeksforgeeks.org/red-black-tree-set-2-insert/)
- [Trực quan hóa Cây Đỏ-Đen](https://www.cs.usfca.edu/~galles/visualization/RedBlack.html)
