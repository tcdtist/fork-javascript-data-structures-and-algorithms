# Bước Nhảy

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

## Bài Toán

Cho một mảng các số nguyên không âm, ban đầu bạn đứng ở
chỉ mục đầu tiên của mảng. Mỗi phần tử trong mảng đại diện cho
độ dài bước nhảy tối đa của bạn tại vị trí đó.

Xác định xem bạn có thể đạt được chỉ mục cuối cùng không.

**Ví dụ #1**

```
Input: [2,3,1,1,4]
Output: true
Giải thích: Nhảy 1 bước từ chỉ mục 0 đến 1, sau đó 3 bước đến chỉ mục cuối cùng.
```

**Ví dụ #2**

```
Input: [3,2,1,0,4]
Output: false
Giải thích: Bạn luôn đến chỉ mục 3 dù cho điều gì. Độ dài bước nhảy tối đa là 0, điều này khiến cho việc đạt được chỉ mục cuối cùng là không thể.
```

## Đặt Tên

Chúng tôi gọi một vị trí trong mảng là **"chỉ mục tốt"** nếu bắt đầu từ vị trí đó,
chúng ta có thể đạt được chỉ mục cuối cùng. Ngược lại, chỉ mục đó được gọi là **"chỉ mục xấu"**.
Vấn đề sau đó thu gọn lại là xem chỉ mục 0 có phải là "chỉ mục tốt" không.

## Các Giải Pháp

### Phương Pháp 1: Quay Lại (Backtracking)

Đây là phương pháp không hiệu quả nơi chúng ta thử mọi cách nhảy từ
vị trí đầu tiên đến cuối cùng. Chúng ta bắt đầu từ vị trí đầu tiên
và nhảy đến mỗi chỉ mục có thể đạt được. Chúng ta lặp lại quá trình cho đến khi cuối
chỉ mục cuối cùng được đạt. Khi bị kẹt, quay lại.

> Xem tập tin [backtrackingJumpGame.js](backtrackingJumpGame.js)

**Độ phức tạp thời gian:** `O(2^n)`.
Có 2<sup>n</sup> (giới hạn trên) cách nhảy từ vị trí đầu tiên đến
cuối cùng, nơi `n` là độ dài của mảng `nums`.

**Độ phức tạp không gian phụ**: `O(n)`.
Đệ quy yêu cầu bộ nhớ bổ sung cho các khung ngăn xếp.

### Phương Pháp 2: Quy Hoạch Động Trên Xuống (Dynamic Programming Top-down)

Quy hoạch động trên xuống có thể được coi là quay lại tối ưu hóa.
Nó dựa trên quan sát rằng một khi chúng ta xác định
rằng một chỉ mục nhất định là tốt / xấu, kết quả này sẽ không bao giờ thay đổi.
Điều này có nghĩa là chúng ta có thể lưu kết quả và không cần phải tính toán lại
nó mỗi lần.

Do đó, đối với mỗi vị trí trong mảng, chúng ta nhớ xem chỉ mục đó có tốt hay xấu không. Hãy gọi mảng này là bảng nhớ và để giá trị của nó là một trong các giá trị sau: GOOD, BAD, UNKNOWN. Kỹ thuật này được gọi là memoization (ghi nhớ).

> Xem tập tin [dpTopDownJumpGame.js](dpTopDownJumpGame.js)

**Độ phức tạp thời gian:** `O(n^2)`.
Đối với mỗi phần tử trong mảng, nói `i`, chúng ta đang xem xét
các phần tử `nums[i]` tiếp theo ở bên phải mục tiêu là tìm chỉ mục tốt. `nums[i]` có thể là tối đa `n`, nơi `n` là độ dài của mảng `nums`.

**Độ phức tạp không gian phụ**: `O(2 * n) = O(n)`.
Đầu tiên `n` xuất phát từ đệ quy. Thứ hai `n` xuất phát từ việc sử dụng bảng memo.

### Phương Pháp 3: Quy Hoạch Động Dưới Lên (Dynamic Programming Bottom-up)

Chuyển từ trên xuống sang dưới được thực hiện bằng cách loại bỏ đệ quy. Trong thực tế, điều này đạt được hiệu suất tốt hơn vì chúng ta không còn bị ảnh hưởng bởi overhead ngăn xếp phương thức và thậm chí còn có thể tận dụng một số bộ nhớ cache. Quan trọng hơn, bước này mở ra các cơ hội tối ưu hóa trong tương lai. Đệ quy thường được loại bỏ bằng cách cố gắng đảo ngược thứ tự các bước từ phương pháp trên xuống.

Quan sát phải là chúng ta chỉ nhảy sang phải. Điều này có nghĩa là nếu chúng ta bắt đầu từ phải của mảng, mỗi khi chúng ta truy vấn một vị trí sang phải của chúng ta, vị trí đó đã được xác định là tốt hoặc xấu. Điều này có nghĩa là chúng ta không cần phải đệ quy nữa, vì chúng ta luôn sẽ đạt được bảng nhớ.

> Xem tập tin [dpBottomUpJumpGame.js](dpBottomUpJumpGame.js)

**Độ phức tạp thời gian:** `O(n^2)`.
Đối với mỗi phần tử trong mảng, nói `i`, chúng ta đang xem xét
các phần tử `nums[i]` tiếp theo ở bên phải mục tiêu là tìm chỉ mục tốt. `nums[i]` có thể là tối đa `n`, nơi `n` là độ dài của mảng `nums`.

**Độ phức tạp không gian phụ**: `O(n)`.
Điều này đến từ việc sử dụng bảng memo.

### Phương Pháp 4: Tham Lam (Greedy)

Khi chúng ta có mã của mình ở trạng thái từ dưới lên, chúng ta có thể thực hiện một quan sát cuối cùng, quan trọng. Từ một vị trí đã cho, khi chúng ta cố gắng xem liệu chúng ta có thể nhảy đến một vị trí TỐT, chúng ta chỉ sử dụng một vị trí - vị trí đầu tiên. Nói cách khác, vị trí cách xa bên trái. Nếu chúng ta tiếp tục theo dõi vị trí TỐT cách xa bên trái như một biến riêng biệt, chúng ta có thể tránh việc tìm kiếm nó trong mảng. Không chỉ vậy, nhưng chúng ta có thể dừng việc sử dụng mảng hoàn toàn.

> Xem tập tin [greedyJumpGame.js](greedyJumpGame.js)

**Độ phức tạp thời gian:** `O(n)`.
Chúng tôi thực hiện một lượt qua mảng `nums`, do đó có `n` bước,
nơi `n` là độ dài của mảng `nums`.

**Độ phức tạp không gian phụ**: `O(1)`.
Chúng tôi không sử dụng bất kỳ bộ nhớ phụ nào.

## Tham Khảo

- [Jump Game Fully Explained trên LeetCode](https://leetcode.com/articles/jump-game/)
- [Dynamic Programming vs Divide and Conquer](https://itnext.io/dynamic-programming-vs-divide-and-conquer-2fea680becbe)
- [Quy Hoạch Động](https://en.wikipedia.org/wiki/Dynamic_programming)
- [Memoization trên Wikipedia](https://en.wikipedia.org/wiki/Memoization)
- [Thiết Kế Từ Trên Xuống và Từ Dưới Lên trên Wikipedia](https://en.wikipedia.org/wiki/Top-down_and_bottom-up_design)
