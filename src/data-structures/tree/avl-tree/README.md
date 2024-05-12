# Cây AVL

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, một **cây AVL** (được đặt theo tên của các nhà phát minh Adelson-Velsky và Landis) là một cây tìm kiếm nhị phân tự cân bằng. Đây là cấu trúc dữ liệu đầu tiên được phát minh trong số đó. Trong một cây AVL, độ cao của hai cây con của bất kỳ nút nào cũng chỉ khác nhau tối đa một; nếu vào bất kỳ thời điểm nào chúng khác nhau hơn một, sẽ được thực hiện cân bằng lại để khôi phục tính chất này. Tìm kiếm, chèn và xóa đều mất `O(log n)` thời gian trong cả trường hợp trung bình và trường hợp xấu nhất, trong đó n là số nút trong cây trước khi thực hiện thao tác. Việc chèn và xóa có thể yêu cầu cây phải được cân bằng lại bằng một hoặc nhiều phép xoay cây.

Hình ảnh động hiển thị việc chèn một số phần tử vào một cây AVL. Nó bao gồm các phép quay trái, phải, trái-phải và phải-trái.

![Cây AVL](https://upload.wikimedia.org/wikipedia/commons/f/fd/AVL_Tree_Example.gif)

Cây AVL với các yếu tố cân bằng (màu xanh lá cây)

![Cây AVL](https://upload.wikimedia.org/wikipedia/commons/a/ad/AVL-tree-wBalance_K.svg)

### Phép Xoay Cây AVL

**Xoay Trái-Trái**

![Xoay Trái-Trái](http://btechsmartclass.com/data_structures/ds_images/LL%20Rotation.png)

**Xoay Phải-Phải**

![Xoay Phải-Phải](http://btechsmartclass.com/data_structures/ds_images/RR%20Rotation.png)

**Xoay Trái-Phải**

![Xoay Trái-Phải](http://btechsmartclass.com/data_structures/ds_images/LR%20Rotation.png)

**Xoay Phải-Trái**

![Xoay Phải-Phải](http://btechsmartclass.com/data_structures/ds_images/RL%20Rotation.png)

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/AVL_tree)
- [Tutorials Point](https://www.tutorialspoint.com/data_structures_algorithms/avl_tree_algorithm.htm)
- [BTech](http://btechsmartclass.com/data_structures/avl-trees.html)
- [Chèn Cây AVL trên YouTube](https://www.youtube.com/watch?v=rbg7Qf8GkQ4&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=12&)
- [Các Trực Quan Hóa Tương Tác của Cây AVL](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)
