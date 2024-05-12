# Đường đi Hamilton

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

**Đường đi Hamilton** (hoặc **đường đi có thể truy vết**) là một đường đi trong một
đồ thị không hướng hoặc có hướng mà đi qua mỗi đỉnh đúng một lần.
Một **chu trình Hamilton** (hoặc **chu trình Hamilton**) là một
đường đi Hamilton tạo thành một chu trình. Xác định xem liệu các đường đi
và chu trình như vậy có tồn tại trong đồ thị hay không là **bài toán đường đi Hamilton**.

![Chu trình Hamilton](https://upload.wikimedia.org/wikipedia/commons/6/6c/Hamiltonian_path_3d.svg)

Một chu trình Hamilton có thể thông qua mọi đỉnh của một
đa diện mười hai mặt được hiển thị bằng màu đỏ - giống như tất cả các hình đa diện đều,
đa diện mười hai mặt là Hamilton.

## Thuật toán Naive

Tạo ra tất cả các cấu hình có thể của các đỉnh và in ra một
cấu hình thỏa mãn các ràng buộc đã cho. Sẽ có
`n!` (n giai thừa) cấu hình.

```
while there are untried configurations
{
   generate the next configuration
   if ( there are edges between two consecutive vertices of this
      configuration and there is an edge from the last vertex to
      the first ).
   {
      print this configuration;
      break;
   }
}
```

## Thuật toán Backtracking

Tạo một mảng đường đi trống và thêm đỉnh `0` vào đó. Thêm các đỉnh
khác, bắt đầu từ đỉnh `1`. Trước khi thêm một đỉnh,
kiểm tra xem nó có kề với đỉnh đã thêm trước đó
và chưa được thêm hay không. Nếu chúng ta tìm thấy một đỉnh như vậy, chúng ta thêm
đỉnh đó làm một phần của giải pháp. Nếu chúng ta không tìm thấy một đỉnh
thì chúng ta trả về false.

## Tham khảo

- [Đường đi Hamilton trên Wikipedia](https://vi.wikipedia.org/wiki/%C4%90%C6%B0%E1%BB%9Dng_%C4%91i_Hamilton)
- [Đường đi Hamilton trên YouTube](https://www.youtube.com/watch?v=dQr4wZCiJJ4&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [Chu trình Hamilton trên GeeksForGeeks](https://www.geeksforgeeks.org/backtracking-set-7-hamiltonian-cycle/)
