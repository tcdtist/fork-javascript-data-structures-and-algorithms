# Cây Tìm Kiếm Nhị Phân

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Trong khoa học máy tính, **cây tìm kiếm nhị phân** (BST), đôi khi được gọi là cây nhị phân được sắp xếp, là một loại đặc biệt của bộ chứa: các cấu trúc dữ liệu lưu trữ "mục" (như số, tên, v.v.) trong bộ nhớ. Chúng cho phép tìm kiếm, thêm và xóa mục một cách nhanh chóng, và có thể được sử dụng để triển khai cả tập hợp động của các mục hoặc bảng tra cứu cho phép tìm một mục bằng khóa của nó (ví dụ, tìm số điện thoại của một người bằng tên).

Cây tìm kiếm nhị phân giữ các khóa của chúng theo thứ tự sắp xếp, để tìm kiếm và các thao tác khác có thể sử dụng nguyên lý của tìm kiếm nhị phân: khi tìm kiếm một khóa trong một cây (hoặc một vị trí để chèn một khóa mới), chúng đi qua cây từ gốc đến lá, so sánh với các khóa được lưu trữ trong các nút của cây và quyết định, dựa trên sự so sánh, để tiếp tục tìm kiếm trong cây con bên trái hoặc bên phải. Trong trung bình, điều này có nghĩa là mỗi sự so sánh cho phép các thao tác bỏ qua khoảng một nửa cây, sao cho mỗi tìm kiếm, chèn hoặc xóa mất thời gian tỷ lệ với logarit của số lượng mục được lưu trữ trong cây. Điều này tốt hơn nhiều so với thời gian tuyến tính cần thiết để tìm các mục theo khóa trong một mảng (chưa được sắp xếp), nhưng chậm hơn so với các thao tác tương ứng trên bảng băm.

Một cây tìm kiếm nhị phân có kích thước 9 và độ sâu 3, với 8 ở gốc. Những lá không được vẽ.

![Trie](./images/binary-search-tree.jpg)

_Tạo bởi [okso.app](https://okso.app)_

## Mã Giả cho Các Thao Tác Cơ Bản

### Chèn

```text
insert(value)
  Pre: value has passed custom type checks for type T
  Post: value has been placed in the correct location in the tree
  if root = ø
    root ← node(value)
  else
    insertNode(root, value)
  end if
end insert
```

```text
insertNode(current, value)
  Pre: current is the node to start from
  Post: value has been placed in the correct location in the tree
  if value < current.value
    if current.left = ø
      current.left ← node(value)
    else
      InsertNode(current.left, value)
    end if
  else
    if current.right = ø
      current.right ← node(value)
    else
      InsertNode(current.right, value)
    end if
  end if
end insertNode
```

### Tìm Kiếm

```text
contains(root, value)
  Pre: root is the root node of the tree, value is what we would like to locate
  Post: value is either located or not
  if root = ø
    return false
  end if
  if root.value = value
    return true
  else if value < root.value
    return contains(root.left, value)
  else
    return contains(root.right, value)
  end if
end contains
```

### Xóa

```text
remove(value)
  Pre: value is the value of the node to remove, root is the node of the BST
      count is the number of items in the BST
  Post: node with value is removed if found in which case yields true, otherwise false
  nodeToRemove ← findNode(value)
  if nodeToRemove = ø
    return false
  end if
  parent ← findParent(value)
  if count = 1
    root ← ø
  else if nodeToRemove.left = ø and nodeToRemove.right = ø
    if nodeToRemove.value < parent.value
      parent.left ←  nodeToRemove.right
    else
      parent.right ← nodeToRemove.right
    end if
  else if nodeToRemove.left != ø and nodeToRemove.right != ø
    next ← nodeToRemove.right
    while next.left != ø
      next ← next.left
    end while
    if next != nodeToRemove.right
      remove(next.value)
      nodeToRemove.value ← next.value
    else
      nodeToRemove.value ← next.value
      nodeToRemove.right ← nodeToRemove.right.right
    end if
  else
    if nodeToRemove.left = ø
      next ← nodeToRemove.right
    else
      next ← nodeToRemove.left
    end if
    if root = nodeToRemove
      root = next
    else if parent.left = nodeToRemove
      parent.left = next
    else if parent.right = nodeToRemove
      parent.right = next
    end if
  end if
  count ← count - 1
  return true
end remove
```

### Tìm Cha của Nút

```text
findParent(value, root)
  Pre: value is the value of the node we want to find the parent of
       root is the root node of the BST and is != ø
  Post: a reference to the prent node of value if found; otherwise ø
  if value = root.value
    return ø
  end if
  if value < root.value
    if root.left = ø
      return ø
    else if root.left.value = value
      return root
    else
      return findParent(value, root.left)
    end if
  else
    if root.right = ø
      return ø
    else if root.right.value = value
      return root
    else
      return findParent(value, root.right)
    end if
  end if
end findParent
```

### Tìm Nút

```text
findNode(root, value)
  Pre: value is the value of the node we want to find the parent of
       root is the root node of the BST
  Post: a reference to the node of value if found; otherwise ø
  if root = ø
    return ø
  end if
  if root.value = value
    return root
  else if value < root.value
    return findNode(root.left, value)
  else
    return findNode(root.right, value)
  end if
end findNode
```

### Tìm Giá Trị Nhỏ Nhất

```text
findMin(root)
  Pre: root is the root node of the BST
    root = ø
  Post: the smallest value in the BST is located
  if root.left = ø
    return root.value
  end if
  findMin(root.left)
end findMin
```

### Tìm Giá Trị Lớn Nhất

```text
findMax(root)
  Pre: root is the root node of the BST
    root = ø
  Post: the largest value in the BST is located
  if root.right = ø
    return root.value
  end if
  findMax(root.right)
end findMax
```

### Duyệt

#### Duyệt theo Trình Tự Trung Tự

```text
inorder(root)
  Pre: root is the root node of the BST
  Post: the nodes in the BST have been visited in inorder
  if root != ø
    inorder(root.left)
    yield root.value
    inorder(root.right)
  end if
end inorder
```

#### Duyệt theo Trình Tự Trước

```text
preorder(root)
  Pre: root is the root node of the BST
  Post: the nodes in the BST have been visited in preorder
  if root != ø
    yield root.value
    preorder(root.left)
    preorder(root.right)
  end if
end preorder
```

#### Duyệt theo Trình Tự Sau

```text
postorder(root)
  Pre: root is the root node of the BST
  Post: the nodes in the BST have been visited in postorder
  if root != ø
    postorder(root.left)
    postorder(root.right)
    yield root.value
  end if
end postorder
```

## Độ Phức Tạp

### Độ Phức Tạp Thời Gian

| Truy Cập  | Tìm Kiếm  |   Chèn    |    Xóa    |
| :-------: | :-------: | :-------: | :-------: |
| O(log(n)) | O(log(n)) | O(log(n)) | O(log(n)) |

### Độ Phức Tạp Không Gian

O(n)

## Tài Liệu Tham Khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Binary_search_tree)
- [Chèn vào BST trên YouTube](https://www.youtube.com/watch?v=wcIRPqTR3Kc&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=9&t=0s)
- [Trực Quan Hóa BST](https://www.cs.usfca.edu/~galles/visualization/BST.html)
