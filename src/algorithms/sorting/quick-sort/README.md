# Sắp xếp nhanh - Quick Sort

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Sắp xếp nhanh là một thuật toán chia để trị.
Sắp xếp nhanh đầu tiên chia một mảng lớn thành hai mảng con nhỏ hơn:
các phần tử thấp và các phần tử cao.
Sắp xếp nhanh sau đó có thể sắp xếp đệ quy các mảng con

Các bước là:

1. Chọn một phần tử, gọi là pivot, từ mảng.
2. Phân chia: sắp xếp lại mảng sao cho tất cả các phần tử có
   giá trị nhỏ hơn pivot đều đứng trước pivot, trong khi tất cả
   các phần tử có giá trị lớn hơn pivot đứng sau nó
   (các giá trị bằng nhau có thể điều này hoặc không). Sau phân chia này,
   pivot nằm ở vị trí cuối cùng của nó. Điều này được gọi là
   phép phân chia.
3. Áp dụng đệ quy các bước trên cho mảng con của
   các phần tử có giá trị nhỏ hơn và riêng biệt cho
   mảng con của các phần tử có giá trị lớn hơn.

Minh họa động của thuật toán sắp xếp nhanh.
Các đường ngang là các giá trị pivot.

![Sắp xếp nhanh](https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif)

## Phức tạp

| Tên               |   Tốt nhất    |  Trung bình   |    Tệ nhất    | Bộ nhớ | Ổn định | Bình luận                                                                  |
| ----------------- | :-----------: | :-----------: | :-----------: | :----: | :-----: | :------------------------------------------------------------------------- |
| **Sắp xếp nhanh** | n&nbsp;log(n) | n&nbsp;log(n) | n<sup>2</sup> | log(n) |  Không  | Sắp xếp nhanh thường được thực hiện tại chỗ với không gian stack O(log(n)) |

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Quicksort)
- [YouTube](https://www.youtube.com/watch?v=SLauY6PpjW4&index=28&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
