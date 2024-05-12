# Ngẫu nhiên có trọng số

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

![Ngẫu nhiên có trọng số](images/cover.png)

## Khái niệm "Ngẫu nhiên có trọng số"

Hãy tưởng tượng bạn có một danh sách các **mục**. Mục có thể là bất cứ thứ gì. Ví dụ, chúng ta có thể có một danh sách các loại hoa quả và rau mà bạn thích ăn: `[ '🍌', '🍎', '🥕' ]`.

Danh sách **trọng số** đại diện cho trọng số (hoặc xác suất, hoặc mức độ quan trọng) của mỗi mục. Trọng số là số. Ví dụ, các trọng số như `[3, 7, 1]` sẽ nói rằng:

- bạn muốn ăn `🍎 táo` thường xuyên hơn (`7` trên tổng số `3 + 7 + 1 = 11` lần),
- sau đó bạn muốn ăn `chuối 🍌` ít hơn (chỉ `3` trên `11` lần),
- và bạn thực sự không thích `cà rốt 🥕` (chỉ muốn ăn nó `1` trong `11` lần).

> Nếu nói về xác suất thì danh sách trọng số có thể là một mảng các số thập phân có tổng bằng `1` (ví dụ: `[0.1, 0.5, 0.2, 0.2]`).

**Ngẫu nhiên có trọng số** trong trường hợp này sẽ là hàm sẽ ngẫu nhiên trả về một mục từ danh sách, và nó sẽ tính đến trọng số của mỗi mục, vì vậy các mục có trọng số cao sẽ được chọn thường xuyên hơn.

Ví dụ về giao diện hàm:

```javascript
const items = ['🍌', '🍎', '🥕'];
const weights = [3, 7, 1];

function weightedRandom(items, weights) {
  // implementation goes here ...
}

const nextSnackToEat = weightedRandom(items, weights); // Có thể là '🍎'
```

## Ứng dụng của Ngẫu nhiên có trọng số

- Trong [Giải thuật di truyền](https://en.wikipedia.org/wiki/Genetic_algorithm) ngẫu nhiên có trọng số được sử dụng trong giai đoạn "Lựa chọn", khi chúng ta cần lựa chọn các cá thể mạnh mẽ/dẻo dai dựa trên điểm thích hợp của họ để giao phối và tạo ra thế hệ tiếp theo mạnh mẽ hơn. Bạn có thể tìm thấy một **ví dụ** trong bài viết [Xe tự đỗ trong 500 dòng mã](https://trekhleb.dev/blog/2021/self-parking-car-evolution/).
- Trong [Mạng nơ-ron tái phát (RNN)](https://en.wikipedia.org/wiki/Recurrent_neural_network) khi cố gắng quyết định chọn chữ cái tiếp theo (để tạo thành câu) dựa trên xác suất chọn chữ cái tiếp theo. Bạn có thể tìm thấy một **ví dụ** trong Jupyter notebook [Tạo ra công thức bằng Mạng nơ-ron tái phát (RNN)](https://nbviewer.org/github/trekhleb/machine-learning-experiments/blob/master/experiments/recipe_generation_rnn/recipe_generation_rnn.ipynb).
- Trong [Cân bằng tải Nginx](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/) để gửi các yêu cầu HTTP thường xuyên hơn đến các máy chủ có trọng số cao hơn.
- Và nhiều hơn nữa...

## Thuật toán

**Cách tiếp cận trực tiếp** sẽ là:

1. Lặp lại mỗi mục trong danh sách theo trọng số của nó.
2. Chọn ngẫu nhiên một mục từ danh sách.

Ví dụ trong trường hợp của chúng ta với hoa quả và rau chúng ta có thể tạo ra danh sách sau với kích thước `3 + 7 + 1 = 11`:

```javascript
const items = ['🍌', '🍎', '🥕'];
const weights = [3, 7, 1];

// Lặp lại các mục dựa trên trọng số.
const weightedItems = [
  '🍌',
  '🍌',
  '🍌',
  '🍎',
  '🍎',
  '🍎',
  '🍎',
  '🍎',
  '🍎',
  '🍎',
  '🥕',
];

// Và bây giờ chỉ cần chọn một mục ngẫu nhiên từ mảng weightedItems.
```

Tuy nhiên, như bạn có thể thấy, cách tiếp cận này có thể yêu cầu rất nhiều bộ nhớ, trong trường hợp nếu chúng ta có nhiều mục cần lặp lại trong danh sách `weightedItems`. Hãy tưởng tượng nếu bạn cần lặp lại một chuỗi như `"một-đoạn-chuỗi-ngẫu-nhiên"` (`18` byte) mười triệu lần. Bạn sẽ cần cấp khoảng `180Mb` bộ nhớ phụ thêm chỉ để mảng này.

**Cách tiếp cận hiệu quả hơn** sẽ là:

1. Chuẩn bị danh sách trọng số tích lũy cho mỗi mục (tức là danh sách `cumulativeWeights` sẽ có cùng số phần tử như danh sách `weights` ban đầu). Trong trường hợp của chúng ta, nó sẽ trông như thế này: `cumulativeWeights = [3, 3 + 7, 3 + 7 + 1] = [3, 10, 11]`.
2. Tạo số ngẫu nhiên `randomNumber` trong khoảng từ `0` đến giá trị trọng số tích lũy cao nhất. Trong trường hợp của chúng ta, số ngẫu nhiên sẽ nằm trong khoảng `[0..11]`. Hãy giả sử rằng chúng ta có `randomNumber = 8`.
3. Duyệt qua danh sách `cumulativeWeights` từ trái sang phải và chọn phần tử đầu tiên mà lớn hơn hoặc bằng `randomNumber`. Chỉ số của phần tử như vậy chúng ta sẽ sử dụng để chọn mục từ mảng `items`.

Ý tưởng đằng sau cách tiếp cận này là các trọng số cao sẽ "chiếm" nhiều không gian số học hơn. Do đó, có khả năng cao rằng số ngẫu nhiên sẽ rơi vào "hộp số cao hơn".

```javascript
const weights = [3, 7, 1];
const cumulativeWeights = [3, 10, 11];

// Trong một biểu diễn giả định chúng ta có thể nghĩ về mảng cumulativeWeights như sau.
const pseudoCumulativeWeights = [
  1,
  2,
  3, // <-- [3] số
  4,
  5,
  6,
  7,
  8,
  9,
  10, // <-- [7] số
  11, // <-- [1] số
];
```

Dưới đây là một ví dụ về cách hàm `weightedRandom` có thể được triển khai:

```javascript
/**
 * Chọn mục ngẫu nhiên dựa trên trọng số của nó.
 * Các mục có trọng số cao sẽ được chọn thường xuyên hơn (với xác suất cao hơn).
 *
 * Ví dụ:
 * - items = ['chuối', 'cam', 'táo']
 * - weights = [0, 0.2, 0.8]
 * - weightedRandom(items, weights) trong 80% trường hợp sẽ trả về 'táo', trong 20% trường hợp sẽ trả về
 * 'cam' và nó sẽ không bao giờ trả về 'chuối' (vì xác suất chọn chuối là 0%)
 *
 * @param {any[]} items
 * @param {number[]} weights
 * @returns {{item: any, index: number}}
 */
export default function weightedRandom(items, weights) {
  if (items.length !== weights.length) {
    throw new Error('Items and weights must be of the same size');
  }

  if (!items.length) {
    throw new Error('Items must not be empty');
  }

  // Chuẩn bị mảng trọng số tích lũy.
  // Ví dụ:
  // - weights = [1, 4, 3]
  // - cumulativeWeights = [1, 5, 8]
  const cumulativeWeights = [];
  for (let i = 0; i < weights.length; i += 1) {
    cumulativeWeights[i] = weights[i] + (cumulativeWeights[i - 1] || 0);
  }

  // Lấy số ngẫu nhiên trong khoảng [0...tổng(weights)]
  // Ví dụ:
  // - weights = [1, 4, 3]
  // - maxCumulativeWeight = 8
  // - phạm vi cho số ngẫu nhiên là [0...8]
  const maxCumulativeWeight = cumulativeWeights[cumulativeWeights.length - 1];
  const randomNumber = maxCumulativeWeight * Math.random();

  // Chọn mục ngẫu nhiên dựa trên trọng số của nó.
  // Các mục có trọng số cao sẽ được chọn thường xuyên.
  for (let itemIndex = 0; itemIndex < items.length; itemIndex += 1) {
    if (cumulativeWeights[itemIndex] >= randomNumber) {
      return {
        item: items[itemIndex],
        index: itemIndex,
      };
    }
  }
}
```

## Triển khai

- Kiểm tra tệp [weightedRandom.js](weightedRandom.js) để xem cách triển khai của hàm `weightedRandom()`.

- Kiểm tra tệp [weightedRandom.test.js](__test__/weightedRandom.test.js) để xem các trường hợp kiểm tra.
