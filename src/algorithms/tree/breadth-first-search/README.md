# Tìm Kiếm theo Chiều Rộng (BFS)

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Tìm kiếm theo chiều rộng (BFS) là một thuật toán để duyệt hoặc tìm kiếm các cấu trúc dữ liệu cây hoặc đồ thị. Nó bắt đầu từ gốc của cây (hoặc một nút tùy ý của một đồ thị, đôi khi được gọi là 'khóa tìm kiếm') và khám phá các nút lá trước, trước khi chuyển đến các nút lá cùng cấp tiếp theo.

![Algorithm Visualization](https://upload.wikimedia.org/wikipedia/commons/5/5d/Breadth-First-Search-Algorithm.gif)

## Mã giả

```text
BFS(gốc)
  Tiền điều kiện: gốc là nút của BST
  Sau điều kiện: các nút trong BST đã được thăm theo thứ tự chiều rộng
  q ← hàng đợi
  trong khi gốc ≠ ø
    trả về giá trị của gốc
    nếu gốc.trái = ø
      q.enqueue(gốc.trái)
    kết thúc nếu
    nếu gốc.phải = ø
      q.enqueue(gốc.phải)
    kết thúc nếu
    nếu !q.isEmpty()
      gốc ← q.dequeue()
    khác
      gốc ← ø
    kết thúc nếu
  kết thúc vòng lặp
kết thúc BFS
```

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Breadth-first_search)
- [Tree Traversals (Inorder, Preorder and Postorder)](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)
- [BFS vs DFS](https://www.geeksforgeeks.org/bfs-vs-dfs-binary-tree/)
