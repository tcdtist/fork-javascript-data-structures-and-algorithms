# Thuật toán và Cấu trúc Dữ liệu JavaScript

[![CI](https://github.com/trekhleb/javascript-algorithms/workflows/CI/badge.svg)](https://github.com/trekhleb/javascript-algorithms/actions?query=workflow%3ACI+branch%3Amaster)
[![codecov](https://codecov.io/gh/trekhleb/javascript-algorithms/branch/master/graph/badge.svg)](https://codecov.io/gh/trekhleb/javascript-algorithms)
![repo size](https://img.shields.io/github/repo-size/trekhleb/javascript-algorithms.svg)

Kho lưu trữ này chứa các ví dụ dựa trên JavaScript
về nhiều thuật toán và cấu trúc dữ liệu phổ biến.

Mỗi thuật toán và cấu trúc dữ liệu đều có một tệp README
riêng với các giải thích liên quan và các liên kết để đọc thêm (bao gồm cả các video trên YouTube).

_Đọc tài liệu này bằng ngôn ngữ khác:_ [_English_](README.en-EN.md)

[Nguồn - Kho lưu trữ gốc](https://github.com/trekhleb/javascript-algorithms)

_☝ Lưu ý rằng dự án này chỉ được sử dụng cho mục đích học tập và nghiên cứu, **không** dùng cho sản xuất._

## Data Structures - Cấu trúc dữ liệu

Cấu trúc dữ liệu là một cách đặc biệt để tổ chức và lưu trữ dữ liệu trong máy tính sao cho có thể truy cập và sửa đổi hiệu quả.
Một cách chính xác hơn, cấu trúc dữ liệu là tập hợp các giá trị dữ liệu,
các mối quan hệ giữa chúng, và các hàm hoặc thao tác có thể được áp dụng cho dữ liệu.

`B` - Người mới bắt đầu, `A` - Nâng cao

- `B` [Linked List - Danh sách liên kết](src/data-structures/linked-list)
- `B` [Doubly Linked List - Danh sách liên kết kép](src/data-structures/doubly-linked-list)
- `B` [Queue - Hàng đợi](src/data-structures/queue)
- `B` [Stack - Ngăn xếp](src/data-structures/stack)
- `B` [Hash Table - Bảng băm](src/data-structures/hash-table)
- `B` [Heap - Đống](src/data-structures/heap) - các phiên bản đống lớn nhất và nhỏ nhất
- `B` [Priority Queue - Hàng đợi ưu tiên](src/data-structures/priority-queue)
- `A` [Trie](src/data-structures/trie)
- `A` [Tree - Cây](src/data-structures/tree)
  - `A` [Binary Search Tree - Cây tìm kiếm nhị phân](src/data-structures/tree/binary-search-tree)
  - `A` [AVL Tree - Cây AVL](src/data-structures/tree/avl-tree)
  - `A` [Red-Black Tree - Cây đỏ đen](src/data-structures/tree/red-black-tree)
  - `A` [Segment Tree - Cây phân đoạn](src/data-structures/tree/segment-tree) - với các ví dụ truy vấn phạm vi tìm min/max/tổng
  - `A` [Fenwick Tree (Binary Indexed Tree) - Cây Fenwick (Cây chỉ số nhị phân)](src/data-structures/tree/fenwick-tree)
- `A` [Graph - Đồ thị](src/data-structures/graph) (cả hai loại có hướng và không hướng)
- `A` [Disjoint Set - Tập hợp rời rạc](src/data-structures/disjoint-set) - cấu trúc dữ liệu hợp nhất–tìm kiếm hoặc tập hợp hợp nhất–tìm kiếm
- `A` [Bloom Filter - Bộ lọc Bloom](src/data-structures/bloom-filter)
- `A` [LRU Cache - Bộ nhớ cache LRU (Least Recently Used)](src/data-structures/lru-cache)

## Algorithms - Thuật toán

Thuật toán là một đặc tả không mơ hồ về cách giải quyết một lớp vấn đề.
Đó là một tập hợp các quy tắc xác định chính xác một chuỗi các thao tác.

`B` - Người mới bắt đầu, `A` - Nâng cao

### Algorithms by Topic - Thuật toán theo Chủ đề

- **Math - Toán học**
  - `B` [Bit Manipulation - Thao tác bit](src/algorithms/math/bits) - đặt/lấy/cập nhật/xóa bit, nhân/chia cho hai, làm số âm, v.v.
  - `B` [Binary Floating Point - Điểm nổi nhị phân](src/algorithms/math/binary-floating-point) - biểu diễn nhị phân của các số dấu phẩy động.
  - `B` [Factorial - Giai thừa](src/algorithms/math/factorial)
  - `B` [Fibonacci Number - Số Fibonacci](src/algorithms/math/fibonacci) - phiên bản cổ điển và phiên bản công thức đóng
  - `B` [Prime Factors - Thừa số nguyên tố](src/algorithms/math/prime-factors) - tìm thừa số nguyên tố và đếm chúng bằng định lý Hardy-Ramanujan
  - `B` [Primality Test - Kiểm tra số nguyên tố](src/algorithms/math/primality-test) (phương pháp chia thử)
  - `B` [Euclidean Algorithm - Thuật toán Euclide](src/algorithms/math/euclidean-algorithm) - tính Ước số chung lớn nhất (GCD)
  - `B` [Least Common Multiple - Bội số chung nhỏ nhất](src/algorithms/math/least-common-multiple) (LCM)
  - `B` [Sieve of Eratosthenes - Rây Eratosthenes](src/algorithms/math/sieve-of-eratosthenes) - tìm tất cả các số nguyên tố đến bất kỳ giới hạn nào được đưa ra
  - `B` [Is Power of Two - Kiểm tra lũy thừa của hai](src/algorithms/math/is-power-of-two) - kiểm tra xem số có phải là lũy thừa của hai không (thuật toán ngây thơ và thuật toán bit)
  - `B` [Pascal's Triangle - Tam giác Pascal](src/algorithms/math/pascal-triangle)
  - `B` [Complex Number - Số phức](src/algorithms/math/complex-number) - các số phức và các phép toán cơ bản với chúng
  - `B` [Radian & Degree - Radian và Độ](src/algorithms/math/radian) - chuyển đổi radian sang độ và ngược lại
  - `B` [Fast Powering - Luỹ thừa nhanh](src/algorithms/math/fast-powering)
  - `B` [Horner's method - Phương pháp Horner](src/algorithms/math/horner-method) - đánh giá đa thức
  - `B` [Matrices - Ma trận](src/algorithms/math/matrix) - ma trận và các thao tác cơ bản với ma trận (nhân, chuyển vị, v.v.)
  - `B` [Euclidean Distance - Khoảng cách Euclide](src/algorithms/math/euclidean-distance) - khoảng cách giữa hai điểm/vectơ/ma trận
  - `A` [Integer Partition - Phân chia số nguyên](src/algorithms/math/integer-partition)
  - `A` [Square Root - Căn bậc hai](src/algorithms/math/square-root) - phương pháp Newton
  - `A` [Liu Hui π Algorithm - Thuật toán π Liu Hui](src/algorithms/math/liu-hui) - tính gần đúng π dựa trên N-gons
  - `A` [Discrete Fourier Transform - Biến đổi Fourier rời rạc](src/algorithms/math/fourier-transform) - phân tích một hàm thời gian (tín hiệu) thành các tần số tạo thành nó
- **Sets - Tập hợp**
  - `B` [Cartesian Product - Tích Descartes](src/algorithms/sets/cartesian-product) - sản phẩm của nhiều tập hợp
  - `B` [Fisher–Yates Shuffle - Xáo trộn Fisher–Yates](src/algorithms/sets/fisher-yates) - hoán vị ngẫu nhiên của một chuỗi hữu hạn
  - `A` [Power Set - Tập lực lượng](src/algorithms/sets/power-set) - tất cả các tập con của một tập hợp (các giải pháp dựa trên bit, backtracking và dâng trào)
  - `A` [Permutations - Hoán vị](src/algorithms/sets/permutations) (có và không có lặp lại)
  - `A` [Combinations - Tổ hợp](src/algorithms/sets/combinations) (có và không có lặp lại)
  - `A` [Longest Common Subsequence - Chuỗi con chung dài nhất](src/algorithms/sets/longest-common-subsequence) (LCS)
  - `A` [Longest Increasing Subsequence - Chuỗi tăng dài nhất](src/algorithms/sets/longest-increasing-subsequence)
  - `A` [Shortest Common Supersequence - Chuỗi chung ngắn nhất](src/algorithms/sets/shortest-common-supersequence) (SCS)
  - `A` [Knapsack Problem - Bài toán ba lô](src/algorithms/sets/knapsack-problem) - các phiên bản "0/1" và "Không giới hạn"
  - `A` [Maximum Subarray - Mảng con lớn nhất](src/algorithms/sets/maximum-subarray) - các phiên bản "Vét cạn" và "Quy hoạch động" (Kadane)
  - `A` [Combination Sum - Tổng các tổ hợp](src/algorithms/sets/combination-sum) - tìm tất cả các tổ hợp tạo thành tổng cụ thể
- **Strings - Chuỗi**
  - `B` [Hamming Distance - Khoảng cách Hamming](src/algorithms/string/hamming-distance) - số lượng vị trí mà các ký tự khác nhau
  - `B` [Palindrome - Chuỗi đối xứng](src/algorithms/string/palindrome) - kiểm tra xem chuỗi có giống nhau khi đảo ngược không
  - `A` [Levenshtein Distance - Khoảng cách Levenshtein](src/algorithms/string/levenshtein-distance) - khoảng cách chỉnh sửa tối thiểu giữa hai chuỗi
  - `A` [Knuth–Morris–Pratt Algorithm (KMP Algorithm) - Thuật toán Knuth–Morris–Pratt](src/algorithms/string/knuth-morris-pratt) - tìm kiếm chuỗi con (so khớp mẫu)
  - `A` [Z Algorithm - Thuật toán Z](src/algorithms/string/z-algorithm) - tìm kiếm chuỗi con (so khớp mẫu)
  - `A` [Rabin Karp Algorithm - Thuật toán Rabin Karp](src/algorithms/string/rabin-karp) - tìm kiếm chuỗi con
  - `A` [Longest Common Substring - Chuỗi con chung dài nhất](src/algorithms/string/longest-common-substring)
  - `A` [Regular Expression Matching - So khớp biểu thức chính quy](src/algorithms/string/regular-expression-matching)
- **Searches - Tìm kiếm**
  - `B` [Linear Search - Tìm kiếm tuyến tính](src/algorithms/search/linear-search)
  - `B` [Jump Search (or Block Search) - Tìm kiếm nhảy (hoặc Tìm kiếm khối)](src/algorithms/search/jump-search) - tìm kiếm trong mảng đã sắp xếp
  - `B` [Binary Search - Tìm kiếm nhị phân](src/algorithms/search/binary-search) - tìm kiếm trong mảng đã sắp xếp
  - `B` [Interpolation Search - Tìm kiếm nội suy](src/algorithms/search/interpolation-search) - tìm kiếm trong mảng đã sắp xếp phân bố đều
- **Sorting - Sắp xếp**
  - `B` [Bubble Sort - Sắp xếp nổi bọt](src/algorithms/sorting/bubble-sort)
  - `B` [Selection Sort - Sắp xếp chọn](src/algorithms/sorting/selection-sort)
  - `B` [Insertion Sort - Sắp xếp chèn](src/algorithms/sorting/insertion-sort)
  - `B` [Heap Sort - Sắp xếp đống](src/algorithms/sorting/heap-sort)
  - `B` [Merge Sort - Sắp xếp trộn](src/algorithms/sorting/merge-sort)
  - `B` [Quicksort - Sắp xếp nhanh](src/algorithms/sorting/quick-sort) - các phiên bản tại chỗ và không tại chỗ
  - `B` [Shellsort - Sắp xếp Shell](src/algorithms/sorting/shell-sort)
  - `B` [Counting Sort - Sắp xếp đếm](src/algorithms/sorting/counting-sort)
  - `B` [Radix Sort - Sắp xếp theo cơ số](src/algorithms/sorting/radix-sort)
  - `B` [Bucket Sort - Sắp xếp thùng](src/algorithms/sorting/bucket-sort)
- **Linked Lists - Danh sách liên kết**
  - `B` [Straight Traversal - Duyệt thẳng](src/algorithms/linked-list/traversal)
  - `B` [Reverse Traversal - Duyệt ngược](src/algorithms/linked-list/reverse-traversal)
- **Trees - Cây**
  - `B` [Depth-First Search - Tìm kiếm theo chiều sâu](src/algorithms/tree/depth-first-search) (DFS)
  - `B` [Breadth-First Search - Tìm kiếm theo chiều rộng](src/algorithms/tree/breadth-first-search) (BFS)
- **Graphs - Đồ thị**
  - `B` [Depth-First Search - Tìm kiếm theo chiều sâu](src/algorithms/graph/depth-first-search) (DFS)
  - `B` [Breadth-First Search - Tìm kiếm theo chiều rộng](src/algorithms/graph/breadth-first-search) (BFS)
  - `B` [Kruskal’s Algorithm - Thuật toán Kruskal](src/algorithms/graph/kruskal) - tìm Cây bao trùm tối thiểu (MST) cho đồ thị vô hướng có trọng số
  - `A` [Dijkstra Algorithm - Thuật toán Dijkstra](src/algorithms/graph/dijkstra) - tìm đường đi ngắn nhất đến tất cả các đỉnh đồ thị từ một đỉnh
  - `A` [Bellman-Ford Algorithm - Thuật toán Bellman-Ford](src/algorithms/graph/bellman-ford) - tìm đường đi ngắn nhất đến tất cả các đỉnh đồ thị từ một đỉnh
  - `A` [Floyd-Warshall Algorithm - Thuật toán Floyd-Warshall](src/algorithms/graph/floyd-warshall) - tìm đường đi ngắn nhất giữa tất cả các cặp đỉnh
  - `A` [Detect Cycle - Phát hiện chu trình](src/algorithms/graph/detect-cycle) - cho cả đồ thị có hướng và không hướng (các phiên bản dựa trên DFS và Tập hợp rời rạc)
  - `A` [Prim’s Algorithm - Thuật toán Prim](src/algorithms/graph/prim) - tìm Cây bao trùm tối thiểu (MST) cho đồ thị vô hướng có trọng số
  - `A` [Topological Sorting - Sắp xếp topo](src/algorithms/graph/topological-sorting) - phương pháp DFS
  - `A` [Articulation Points - Điểm nối](src/algorithms/graph/articulation-points) - thuật toán Tarjan (dựa trên DFS)
  - `A` [Bridges - Cầu](src/algorithms/graph/bridges) - thuật toán dựa trên DFS
  - `A` [Eulerian Path and Eulerian Circuit - Đường đi Euler và Chu trình Euler](src/algorithms/graph/eulerian-path) - thuật toán Fleury - ghé thăm mỗi cạnh một lần
  - `A` [Hamiltonian Cycle - Chu trình Hamilton](src/algorithms/graph/hamiltonian-cycle) - ghé thăm mỗi đỉnh một lần
  - `A` [Strongly Connected Components - Thành phần liên thông mạnh](src/algorithms/graph/strongly-connected-components) - thuật toán Kosaraju
  - `A` [Travelling Salesman Problem - Bài toán người bán hàng du lịch](src/algorithms/graph/travelling-salesman) - tuyến đường ngắn nhất có thể ghé thăm mỗi thành phố và trở về thành phố xuất phát
- **Cryptography - Mật mã học**
  - `B` [Polynomial Hash - Băm đa thức](src/algorithms/cryptography/polynomial-hash) - hàm băm dựa trên đa thức
  - `B` [Rail Fence Cipher - Mật mã hàng rào](src/algorithms/cryptography/rail-fence-cipher) - thuật toán mật mã hoán vị để mã hóa tin nhắn
  - `B` [Caesar Cipher - Mật mã Caesar](src/algorithms/cryptography/caesar-cipher) - mật mã thay thế đơn giản
  - `B` [Hill Cipher - Mật mã Hill](src/algorithms/cryptography/hill-cipher) - mật mã thay thế dựa trên đại số tuyến tính
- **Machine Learning - Máy học**
  - `B` [NanoNeuron](https://github.com/trekhleb/nano-neuron) - 7 hàm JS đơn giản minh họa cách máy móc có thể học hỏi thực sự (lan truyền tiến/lùi)
  - `B` [k-NN - k-Nearest Neighbors](src/algorithms/ml/knn) - thuật toán phân loại k láng giềng gần nhất
  - `B` [k-Means - k-Means](src/algorithms/ml/k-means) - thuật toán phân cụm k-Means
- **Image Processing - Xử lý ảnh**
  - `B` [Seam Carving - Cắt chỉnh sửa nội dung](src/algorithms/image-processing/seam-carving) - thuật toán thay đổi kích thước ảnh nhận thức nội dung
- **Statistics - Thống kê**
  - `B` [Weighted Random - Ngẫu nhiên có trọng số](src/algorithms/statistics/weighted-random) - chọn mục ngẫu nhiên từ danh sách dựa trên trọng số của các mục
- **Evolutionary algorithms - Thuật toán tiến hóa**
  - `A` [Genetic algorithm - Thuật toán di truyền](https://github.com/trekhleb/self-parking-car-evolution) - ví dụ về cách áp dụng thuật toán di truyền để huấn luyện xe tự đỗ
- **Uncategorized - Không phân loại**
  - `B` [Tower of Hanoi - Tháp Hà Nội](src/algorithms/uncategorized/hanoi-tower)
  - `B` [Square Matrix Rotation - Xoay ma trận vuông](src/algorithms/uncategorized/square-matrix-rotation) - thuật toán tại chỗ
  - `B` [Jump Game - Trò chơi nhảy](src/algorithms/uncategorized/jump-game) - các ví dụ về vét cạn, quy hoạch động (trên xuống + dưới lên) và tham lam
  - `B` [Unique Paths - Đường đi độc đáo](src/algorithms/uncategorized/unique-paths) - các ví dụ về vét cạn, quy hoạch động và Tam giác Pascal
  - `B` [Rain Terraces - Mái hiên mưa](src/algorithms/uncategorized/rain-terraces) - bài toán mắc kẹt nước mưa (quy hoạch động và các phiên bản vét cạn)
  - `B` [Recursive Staircase - Cầu thang đệ quy](src/algorithms/uncategorized/recursive-staircase) - đếm số cách để đạt đến đỉnh (4 giải pháp)
  - `B` [Best Time To Buy Sell Stocks - Thời điểm tốt nhất để mua bán cổ phiếu](src/algorithms/uncategorized/best-time-to-buy-sell-stocks) - chia để trị và các ví dụ một lần
  - `A` [N-Queens Problem - Bài toán N quân hậu](src/algorithms/uncategorized/n-queens)
  - `A` [Knight's Tour - Chuyến du lịch của hiệp sĩ](src/algorithms/uncategorized/knight-tour)

### Algorithms by Paradigm - Thuật toán theo Mô hình

Một mô hình thuật toán là một phương pháp chung hoặc cách tiếp cận chung chung cho thiết kế một loạt thuật toán.
Nó là một trừu tượng cao hơn so với khái niệm thuật toán,
giống như thuật toán là một trừu tượng cao hơn so với chương trình máy tính.

- **Brute Force - Vét cạn** - xem xét tất cả các khả năng và chọn giải pháp tốt nhất
  - `B` [Linear Search - Tìm kiếm tuyến tính](src/algorithms/search/linear-search)
  - `B` [Rain Terraces - Mái hiên mưa](src/algorithms/uncategorized/rain-terraces) - bài toán mắc kẹt nước mưa
  - `B` [Recursive Staircase - Cầu thang đệ quy](src/algorithms/uncategorized/recursive-staircase) - đếm số cách để đạt đến đỉnh
  - `A` [Maximum Subarray - Mảng con lớn nhất](src/algorithms/sets/maximum-subarray)
  - `A` [Travelling Salesman Problem - Bài toán người bán hàng du lịch](src/algorithms/graph/travelling-salesman) - tuyến đường ngắn nhất có thể ghé thăm mỗi thành phố và trở về thành phố xuất phát
  - `A` [Discrete Fourier Transform - Biến đổi Fourier rời rạc](src/algorithms/math/fourier-transform) - phân tích một hàm thời gian (tín hiệu) thành các tần số tạo thành nó
- **Greedy - Tham lam** - chọn giải pháp tốt nhất tại thời điểm hiện tại, mà không cần xem xét đến tương lai
  - `B` [Jump Game - Trò chơi nhảy](src/algorithms/uncategorized/jump-game)
  - `A` [Unbound Knapsack Problem - Bài toán ba lô không giới hạn](src/algorithms/sets/knapsack-problem)
  - `A` [Dijkstra Algorithm - Thuật toán Dijkstra](src/algorithms/graph/dijkstra) - tìm đường đi ngắn nhất đến tất cả các đỉnh đồ thị
  - `A` [Prim’s Algorithm - Thuật toán Prim](src/algorithms/graph/prim) - tìm Cây bao trùm tối thiểu (MST) cho đồ thị vô hướng có trọng số
  - `A` [Kruskal’s Algorithm - Thuật toán Kruskal](src/algorithms/graph/kruskal) - tìm Cây bao trùm tối thiểu (MST) cho đồ thị vô hướng có trọng số
- **Divide and Conquer - Chia để trị** - chia vấn đề thành các phần nhỏ hơn và sau đó giải quyết những phần đó
  - `B` [Binary Search - Tìm kiếm nhị phân](src/algorithms/search/binary-search)
  - `B` [Tower of Hanoi - Tháp Hà Nội](src/algorithms/uncategorized/hanoi-tower)
  - `B` [Pascal's Triangle - Tam giác Pascal](src/algorithms/math/pascal-triangle)
  - `B` [Euclidean Algorithm - Thuật toán Euclide](src/algorithms/math/euclidean-algorithm) - tính Ước số chung lớn nhất (GCD)
  - `B` [Merge Sort - Sắp xếp trộn](src/algorithms/sorting/merge-sort)
  - `B` [Quicksort - Sắp xếp nhanh](src/algorithms/sorting/quick-sort)
  - `B` [Tree Depth-First Search - Tìm kiếm theo chiều sâu cây](src/algorithms/tree/depth-first-search) (DFS)
  - `B` [Graph Depth-First Search - Tìm kiếm theo chiều sâu đồ thị](src/algorithms/graph/depth-first-search) (DFS)
  - `B` [Matrices - Ma trận](src/algorithms/math/matrix) - tạo và duyệt các ma trận có hình dạng khác nhau
  - `B` [Jump Game - Trò chơi nhảy](src/algorithms/uncategorized/jump-game)
  - `B` [Fast Powering - Luỹ thừa nhanh](src/algorithms/math/fast-powering)
  - `B` [Best Time To Buy Sell Stocks - Thời điểm tốt nhất để mua bán cổ phiếu](src/algorithms/uncategorized/best-time-to-buy-sell-stocks) - chia để trị và các ví dụ một lần
  - `A` [Permutations - Hoán vị](src/algorithms/sets/permutations) (có và không có lặp lại)
  - `A` [Combinations - Tổ hợp](src/algorithms/sets/combinations) (có và không có lặp lại)
  - `A` [Maximum Subarray - Mảng con lớn nhất](src/algorithms/sets/maximum-subarray)
- **Dynamic Programming - Quy hoạch động** - xây dựng giải pháp sử dụng các tiểu giải pháp đã tìm thấy trước đó
  - `B` [Fibonacci Number - Số Fibonacci](src/algorithms/math/fibonacci)
  - `B` [Jump Game - Trò chơi nhảy](src/algorithms/uncategorized/jump-game)
  - `B` [Unique Paths - Đường đi độc đáo](src/algorithms/uncategorized/unique-paths)
  - `B` [Rain Terraces - Mái hiên mưa](src/algorithms/uncategorized/rain-terraces) - bài toán mắc kẹt nước mưa
  - `B` [Recursive Staircase - Cầu thang đệ quy](src/algorithms/uncategorized/recursive-staircase) - đếm số cách để đạt đến đỉnh
  - `B` [Seam Carving - Cắt chỉnh sửa nội dung](src/algorithms/image-processing/seam-carving) - thuật toán thay đổi kích thước ảnh nhận thức nội dung
  - `A` [Levenshtein Distance - Khoảng cách Levenshtein](src/algorithms/string/levenshtein-distance) - khoảng cách chỉnh sửa tối thiểu giữa hai chuỗi
  - `A` [Longest Common Subsequence - Chuỗi con chung dài nhất](src/algorithms/sets/longest-common-subsequence) (LCS)
  - `A` [Longest Common Substring - Chuỗi con chung dài nhất](src/algorithms/string/longest-common-substring)
  - `A` [Longest Increasing Subsequence - Chuỗi tăng dài nhất](src/algorithms/sets/longest-increasing-subsequence)
  - `A` [Shortest Common Supersequence - Chuỗi chung ngắn nhất](src/algorithms/sets/shortest-common-supersequence)
  - `A` [0/1 Knapsack Problem - Bài toán ba lô 0/1](src/algorithms/sets/knapsack-problem)
  - `A` [Integer Partition - Phân chia số nguyên](src/algorithms/math/integer-partition)
  - `A` [Maximum Subarray - Mảng con lớn nhất](src/algorithms/sets/maximum-subarray)
  - `A` [Bellman-Ford Algorithm - Thuật toán Bellman-Ford](src/algorithms/graph/bellman-ford) - tìm đường đi ngắn nhất đến tất cả các đỉnh đồ thị
  - `A` [Floyd-Warshall Algorithm - Thuật toán Floyd-Warshall](src/algorithms/graph/floyd-warshall) - tìm đường đi ngắn nhất giữa tất cả các cặp đỉnh
  - `A` [Regular Expression Matching - So khớp biểu thức chính quy](src/algorithms/string/regular-expression-matching)
- **Backtracking** - tương tự như vét cạn, thử tạo ra tất cả các giải pháp có thể, nhưng mỗi lần bạn tạo ra giải pháp tiếp theo,
  bạn kiểm tra xem nó có đáp ứng tất cả các điều kiện không và chỉ sau đó mới tiếp tục tạo ra các giải pháp tiếp theo.
  Nếu không, quay lại và đi theo một hướng khác để tìm giải pháp. Thường thì duyệt không gian trạng thái bằng DFS được sử dụng.
- `B` [Jump Game - Trò chơi nhảy](src/algorithms/uncategorized/jump-game)
- `B` [Unique Paths - Đường đi độc đáo](src/algorithms/uncategorized/unique-paths)
- `B` [Power Set - Tập lực lượng](src/algorithms/sets/power-set) - tất cả các tập con của một tập hợp
- `A` [Hamiltonian Cycle - Chu trình Hamilton](src/algorithms/graph/hamiltonian-cycle) - Ghé thăm mỗi đỉnh một lần
- `A` [N-Queens Problem - Bài toán N quân hậu](src/algorithms/uncategorized/n-queens)
- `A` [Knight's Tour - Chuyến du lịch của hiệp sĩ](src/algorithms/uncategorized/knight-tour)
- `A` [Combination Sum - Tổng các tổ hợp](src/algorithms/sets/combination-sum) - tìm tất cả các tổ hợp tạo thành tổng cụ thể
- **Branch & Bound** - nhớ giải pháp có chi phí thấp nhất tìm thấy ở mỗi giai đoạn của quá trình backtracking,
  và sử dụng chi phí của giải pháp có chi phí thấp nhất tìm thấy cho đến nay làm ranh giới dưới
  về chi phí của giải pháp ít chi phí nhất cho vấn đề,
  để loại bỏ các giải pháp một phần có chi phí lớn hơn giải pháp có chi phí thấp nhất tìm thấy cho đến nay.
  Thường thì duyệt không gian trạng thái cây bằng BFS kết hợp với duyệt DFS được sử dụng.

## How to use this repository - Cách sử dụng kho lưu trữ này

**Install all dependencies - Cài đặt tất cả các phụ thuộc**

```
npm install
```

**Run ESLint - Chạy ESLint**

Bạn có thể muốn chạy nó để kiểm tra chất lượng mã.

```
npm run lint
```

**Run all tests - Chạy tất cả các bài kiểm tra**

```
npm test
```

**Run tests by name - Chạy các bài kiểm tra theo tên**

```
npm test -- 'LinkedList'
```

**Troubleshooting - Khắc phục sự cố**

Nếu việc linting hoặc kiểm tra thất bại, hãy thử xóa thư mục `node_modules` và cài đặt lại các gói npm:

```
rm -rf ./node_modules
npm i
```

Cũng đảm bảo rằng bạn đang sử dụng phiên bản Node đúng (`>=16`). Nếu bạn đang sử dụng [nvm](https://github.com/nvm-sh/nvm) để quản lý phiên bản Node, bạn có thể chạy `nvm use` từ thư mục gốc của dự án và phiên bản đúng sẽ được chọn.

**Playground - Sân chơi**

Bạn có thể chơi với các cấu trúc dữ liệu và thuật toán trong tệp `./src/playground/playground.js`
và viết các bài kiểm tra cho nó trong `./src/playground/__test__/playground.test.js`.

Sau đó chỉ cần chạy lệnh sau để kiểm tra xem mã sân chơi của bạn có hoạt động như mong đợi hay không:

```
npm test -- 'playground'
```

## Useful Information - Thông tin hữu ích

### References - Tài liệu tham khảo

- [▶ Cấu trúc dữ liệu và Thuật toán trên YouTube](https://www.youtube.com/playlist?list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [✍🏻 Bản vẽ Cấu trúc dữ liệu](https://okso.app/showcase/data-structures)

### Big O Notation - Ký hiệu Big O

_Ký hiệu Big O_ được sử dụng để phân loại các thuật toán theo cách thời gian chạy hoặc yêu cầu không gian của chúng tăng lên như thế nào khi kích thước đầu vào tăng lên.
Trên biểu đồ dưới đây, bạn có thể tìm thấy các trật tự tăng trưởng phổ biến nhất của các thuật toán được chỉ định trong ký hiệu Big O.

![Biểu đồ Big O](./assets/big-o-graph.png)

Nguồn: [Big O Cheat Sheet](http://bigocheatsheet.com/).

Dưới đây là danh sách một số ký hiệu Big O phổ biến nhất và so sánh hiệu suất của chúng đối với các kích thước dữ liệu đầu vào khác nhau.

| Big O Notation | Type        | Computations for 10 elements | Computations for 100 elements | Computations for 1000 elements |
| -------------- | ----------- | ---------------------------- | ----------------------------- | ------------------------------ |
| **O(1)**       | Constant    | 1                            | 1                             | 1                              |
| **O(log N)**   | Logarithmic | 3                            | 6                             | 9                              |
| **O(N)**       | Linear      | 10                           | 100                           | 1000                           |
| **O(N log N)** | n log(n)    | 30                           | 600                           | 9000                           |
| **O(N^2)**     | Quadratic   | 100                          | 10000                         | 1000000                        |
| **O(2^N)**     | Exponential | 1024                         | 1.26e+29                      | 1.07e+301                      |
| **O(N!)**      | Factorial   | 3628800                      | 9.3e+157                      | 4.02e+2567                     |

### Data Structure Operations Complexity

| Data Structure         | Access | Search | Insertion | Deletion | Comments                                             |
| ---------------------- | :----: | :----: | :-------: | :------: | :--------------------------------------------------- |
| **Array**              |   1    |   n    |     n     |    n     |                                                      |
| **Stack**              |   n    |   n    |     1     |    1     |                                                      |
| **Queue**              |   n    |   n    |     1     |    1     |                                                      |
| **Linked List**        |   n    |   n    |     1     |    n     |                                                      |
| **Hash Table**         |   -    |   n    |     n     |    n     | In case of perfect hash function costs would be O(1) |
| **Binary Search Tree** |   n    |   n    |     n     |    n     | In case of balanced tree costs would be O(log(n))    |
| **B-Tree**             | log(n) | log(n) |  log(n)   |  log(n)  |                                                      |
| **Red-Black Tree**     | log(n) | log(n) |  log(n)   |  log(n)  |                                                      |
| **AVL Tree**           | log(n) | log(n) |  log(n)   |  log(n)  |                                                      |
| **Bloom Filter**       |   -    |   1    |     1     |    -     | False positives are possible while searching         |

### Array Sorting Algorithms Complexity

| Name               |     Best      |         Average         |            Worst            | Memory | Stable | Comments                                                      |
| ------------------ | :-----------: | :---------------------: | :-------------------------: | :----: | :----: | :------------------------------------------------------------ |
| **Bubble sort**    |       n       |      n<sup>2</sup>      |        n<sup>2</sup>        |   1    |  Yes   |                                                               |
| **Insertion sort** |       n       |      n<sup>2</sup>      |        n<sup>2</sup>        |   1    |  Yes   |                                                               |
| **Selection sort** | n<sup>2</sup> |      n<sup>2</sup>      |        n<sup>2</sup>        |   1    |   No   |                                                               |
| **Heap sort**      | n&nbsp;log(n) |      n&nbsp;log(n)      |        n&nbsp;log(n)        |   1    |   No   |                                                               |
| **Merge sort**     | n&nbsp;log(n) |      n&nbsp;log(n)      |        n&nbsp;log(n)        |   n    |  Yes   |                                                               |
| **Quick sort**     | n&nbsp;log(n) |      n&nbsp;log(n)      |        n<sup>2</sup>        | log(n) |   No   | Quicksort is usually done in-place with O(log(n)) stack space |
| **Shell sort**     | n&nbsp;log(n) | depends on gap sequence | n&nbsp;(log(n))<sup>2</sup> |   1    |   No   |                                                               |
| **Counting sort**  |     n + r     |          n + r          |            n + r            | n + r  |  Yes   | r - biggest number in array                                   |
| **Radix sort**     |    n \* k     |         n \* k          |           n \* k            | n + k  |  Yes   | k - length of longest key                                     |

## Project Backers - Nhà tài trợ dự án

> Bạn có thể hỗ trợ dự án này qua ❤️️ [GitHub](https://github.com/sponsors/trekhleb) hoặc ❤️️ [Patreon](https://www.patreon.com/trekhleb).

[Những người đang tài trợ cho dự án này](https://github.com/trekhleb/javascript-algorithms/blob/master/BACKERS.md) `∑ = 1`

## Author - Tác giả

[@trekhleb](https://trekhleb.dev)

Thêm một số [dự án](https://trekhleb.dev/projects/) và [bài viết](https://trekhleb.dev/blog/) về JavaScript và thuật toán tại [trekhleb.dev](https://trekhleb.dev)
