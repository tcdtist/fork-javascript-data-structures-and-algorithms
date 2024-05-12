# Thời điểm Tốt Nhất để Mua và Bán Cổ Phiếu

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

## Mô tả Công Việc

Cho một mảng giá cổ phiếu trong đó phần tử thứ `i` là giá của một cổ phiếu cụ thể vào ngày `i`.

Tìm lợi nhuận lớn nhất có thể. Bạn có thể thực hiện bất kỳ số giao dịch nào bạn muốn (tức là, mua và bán một cổ phiếu nhiều lần).

> Lưu ý: Bạn không thể tham gia nhiều giao dịch cùng một lúc (tức là, bạn phải bán cổ phiếu trước khi mua lại).

**Ví dụ #1**

```
Input: [7, 1, 5, 3, 6, 4]
Output: 7
```

_Giải thích:_ Mua vào ngày `2` (`giá = 1`) và bán vào ngày `3` (`giá = 5`), `lợi nhuận = 5-1 = 4`. Sau đó mua vào ngày `4` (`giá = 3`) và bán vào ngày `5` (`giá = 6`), `lợi nhuận = 6-3 = 3`.

**Ví dụ #2**

```
Input: [1, 2, 3, 4, 5]
Output: 4
```

_Giải thích:_ Mua vào ngày `1` (`giá = 1`) và bán vào ngày `5` (`giá = 5`), `lợi nhuận = 5-1 = 4`. Lưu ý rằng bạn không thể mua vào ngày 1, mua vào ngày 2 và sau đó bán chúng sau này, vì bạn đang tham gia nhiều giao dịch cùng một lúc. Bạn phải bán trước khi mua lại.

**Ví dụ #3**

```
Input: [7, 6, 4, 3, 1]
Output: 0
```

_Giải thích:_ Trong trường hợp này, không có giao dịch nào được thực hiện, tức là lợi nhuận tối đa `lợi nhuận = 0`.

## Các Giải Pháp Có Thể

### Tiếp Cận Chia và Trị `O(2^n)`

Chúng ta có thể thử **tất cả** các kết hợp mua và bán và tìm ra kết quả có lợi nhuận lớn nhất bằng cách áp dụng _tiếp cận chia và trị_.

Hãy giả sử chúng ta có một mảng giá `[7, 6, 4, 3, 1]` và chúng ta đang ở _ngày thứ nhất_ của giao dịch (tại điểm bắt đầu của mảng). Tại thời điểm này, chúng ta có thể nói rằng tổng lợi nhuận toàn bộ sẽ là _lớn nhất_ của hai giá trị sau:

1. _Tùy chọn 1: Giữ lại tiền_ → lợi nhuận sẽ bằng lợi nhuận từ việc mua/bán cổ phiếu còn lại → `keepProfit = profit([6, 4, 3, 1])`.
2. _Tùy chọn 2: Mua/bán tại giá hiện tại_ → lợi nhuận trong trường hợp này sẽ bằng lợi nhuận từ việc mua/bán cổ phiếu còn lại cộng (hoặc trừ, phụ thuộc vào việc chúng ta bán hay mua) giá cổ phiếu hiện tại → `buySellProfit = -7 + profit([6, 4, 3, 1])`.

Tổng lợi nhuận sẽ bằng → `overalProfit = Max(keepProfit, buySellProfit)`.

Như bạn có thể thấy nhiệm vụ `profit([6, 4, 3, 1])` được giải quyết theo cùng một cách đệ quy.

> Xem ví dụ mã đầy đủ tại [dqBestTimeToBuySellStocks.js](dqBestTimeToBuySellStocks.js)

#### Độ Phức Tạp Thời Gian

Như bạn có thể thấy, mỗi lời gọi đệ quy sẽ tạo ra _2_ nhánh đệ quy nữa. Độ sâu của đệ quy sẽ là `n` (kích thước của mảng giá) và do đó, độ phức tạp thời gian sẽ bằng `O(2^n)`.

Như bạn có thể thấy, điều này rất không hiệu quả. Ví dụ, chỉ cần `20` giá trị thì số lời gọi đệ quy sẽ gần bằng `2M`!

#### Độ Phức Tạp Không Gian Bổ Sung

Nếu chúng ta tránh việc sao chép mảng giá giữa các lời gọi hàm đệ quy và sử dụng con trỏ mảng thì độ phức tạp không gian bổ sung sẽ tỉ lệ với độ sâu của đệ quy: `O(n)`.

## Tiếp Cận Đỉnh Thung Lũng `O(n)`

Nếu chúng ta vẽ biểu đồ của mảng giá (ví dụ: `[7, 1, 5, 3, 6, 4]`) thì chúng ta có thể nhận thấy các điểm quan trọng là các thung lũng và đỉnh liên tiếp

![Tiếp Cận Đỉnh Thung Lũng](https://leetcode.com/media/original_images/122_maxprofit_1.PNG)

_Nguồn hình ảnh: [LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/solution/)_

Vì vậy, nếu chúng ta theo dõi giá tăng và bán cổ phiếu ngay _trước khi_ giá giảm xuống, chúng ta sẽ nhận được lợi nhuận tối đa (hãy nhớ, chúng ta mua cổ phiếu ở thung lũng với giá thấp của nó).

> Xem ví dụ mã đầy đủ tại [peakvalleyBestTimeToBuySellStocks.js](peakvalleyBestTimeToBuySellStocks.js)

#### Độ Phức Tạp Thời Gian

Vì thuật toán chỉ yêu cầu một lần duyệt qua mảng giá, do đó độ phức tạp thời gian sẽ bằng `O(n)`.

#### Độ Phức Tạp Không Gian Bổ Sung

Ngoài mảng giá chính nó, thuật toán chỉ tiêu thụ một lượng bộ nhớ cố định. Do đó, độ phức tạp không gian bổ sung là `O(1)`.

## Tiếp Cận Tích Lũy `O(n)`

Còn một cách tiếp cận đơn giản hơn tồn tại. Hãy giả sử chúng ta có mảng giá như sau `[1, 7, 2, 3, 6, 7, 6, 7]`:

![Duyệt Một Lần](https://leetcode.com/media/original_images/122_maxprofit_2.PNG)

_Nguồn hình ảnh: [LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/solution/)_

Bạn có thể nhận thấy, chúng ta thậm chí không cần theo dõi một giá cả liên tục tăng. Thay vào đó, chúng ta có thể đơn giản là thêm số chênh lệch giá cho _tất cả các đoạn liên tiếp_ của biểu đồ mà tăng giá, điều này cuối cùng sẽ cộng lại thành lợi nhuận cao nhất có thể,

> Xem ví dụ mã đầy đủ tại [accumulatorBestTimeToBuySellStocks.js](accumulatorBestTimeToBuySellStocks.js)

#### Độ Phức Tạp Thời Gian

Vì thuật toán chỉ yêu cầu một lần duyệt qua mảng giá, do đó độ phức tạp thời gian sẽ bằng `O(n)`.

#### Độ Phức Tạp Không Gian Bổ Sung

Ngoài mảng giá chính nó, thuật toán chỉ tiêu thụ một lượng bộ nhớ cố định. Do đó, độ phức tạp không gian bổ sung là `O(1)`.

## Tham Khảo

- [Thời Điểm Tốt Nhất để Mua và Bán Cổ Phiếu trên LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)
