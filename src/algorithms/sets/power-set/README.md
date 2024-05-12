# Tập con lớn nhất

_Đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Tập con lớn nhất (Power set) của một tập hợp `S` là tập hợp của tất cả các tập con của `S`, bao gồm cả tập rỗng và `S` chính nó. Tập con lớn nhất của tập hợp `S` được ký hiệu là `P(S)`.

Ví dụ với `{x, y, z}`, các tập con là:

```text
{
  {}, // (cũng được ký hiệu là tập rỗng ∅ hoặc tập con null)
  {x},
  {y},
  {z},
  {x, y},
  {x, z},
  {y, z},
  {x, y, z}
}
```

![Tập con lớn nhất](https://www.mathsisfun.com/sets/images/power-set.svg)

Dưới đây là cách chúng ta có thể minh họa các phần tử của tập con lớn nhất của tập hợp `{x, y, z}` được sắp xếp theo thứ tự bao gồm:

![](https://upload.wikimedia.org/wikipedia/commons/e/ea/Hasse_diagram_of_powerset_of_3.svg)

**Số lượng Tập con**

Nếu `S` là một tập hợp hữu hạn có `|S| = n` phần tử, thì số lượng tập con của `S` là `|P(S)| = 2^n`. Sự thật này, là động lực cho ký hiệu `2^S`, có thể được chứng minh một cách đơn giản như sau:

> Trước tiên, sắp xếp các phần tử của `S` theo bất kỳ cách nào. Chúng ta viết bất kỳ tập con của `S` nào trong định dạng `{γ1, γ2, ..., γn}` với `γi , 1 ≤ i ≤ n`, có thể nhận giá trị là `0` hoặc `1`. Nếu `γi = 1`, phần tử thứ `i` của `S` được chọn; ngược lại, phần tử thứ `i` không được chọn. Rõ ràng số lượng tập con riêng biệt có thể được xây dựng theo cách này là `2^n` vì `γi ∈ {0, 1}`.

## Thuật toán

### Giải pháp Bitwise

Mỗi số trong biểu diễn nhị phân trong khoảng từ `0` đến `2^n` chính xác làm những gì chúng ta cần: nó cho biết bằng các bit (`0` hoặc `1`) liệu có nên bao gồm phần tử tương ứng từ tập hợp hay không. Ví dụ, đối với tập hợp `{1, 2, 3}` số nhị phân `0b010` sẽ cho biết rằng chúng ta cần chỉ bao gồm `2` vào tập hiện tại.

|     | `abc` |   Tập con   |
| :-: | :---: | :---------: |
| `0` | `000` |    `{}`     |
| `1` | `001` |    `{c}`    |
| `2` | `010` |    `{b}`    |
| `3` | `011` |  `{c, b}`   |
| `4` | `100` |    `{a}`    |
| `5` | `101` |  `{a, c}`   |
| `6` | `110` |  `{a, b}`   |
| `7` | `111` | `{a, b, c}` |

> Xem tệp [bwPowerSet.js](./bwPowerSet.js) cho giải pháp bitwise.

### Giải pháp Backtracking

Trong phương pháp quay lui, chúng ta liên tục cố gắng thêm phần tử tiếp theo của tập hợp vào tập con, ghi nhớ nó và sau đó loại bỏ nó và thử cùng với phần tử tiếp theo.

> Xem tệp [btPowerSet.js](./btPowerSet.js) cho giải pháp backtracking.

### Giải pháp Lan truyền

Đây có lẽ là giải pháp đơn giản nhất để tạo ra một tập con lớn nhất.

Chúng ta bắt đầu với một tập hợp rỗng:

```text
powerSets = [[]]
```

Bây giờ, giả sử:

```text
tập ban đầu = [1, 2, 3]
```

Thêm phần tử thứ nhất từ tập ban đầu vào tất cả các tập con hiện có:

```text
[[]] ← 1 = [[], [1]]
```

Thêm phần tử thứ hai vào tất cả các tập con hiện có:

```text
[[], [1]] ← 2 = [[], [1], [2], [1, 2]]
```

Thêm phần tử thứ ba vào tất cả các tập con hiện có:

```
[[], [1], [2], [1, 2]] ← 3 = [[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]
```

Và tiếp tục như vậy, cho đến phần còn lại của các phần tử từ `tập ban đầu`. Trong mỗi lần lặp lại, số lượng tập được nhân đôi, vì vậy chúng ta sẽ có `2^n` tập.

> Xem tệp [caPowerSet.js](./caPowerSet.js) cho giải pháp cascading.

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Power_set)
- [Math is Fun](https://www.mathsisfun.com/sets/power-set.html)
