# Thay Đổi Kích Thước Hình Ảnh Có Ý Thức Về Nội Dung Trong JavaScript

_Xem bằng các ngôn ngữ khác:_
[_Tiếng Anh_](README.en.md)

![Thay Đổi Kích Thước Hình Ảnh Có Ý Thức Về Nội Dung Trong JavaScript](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/01-cover-02.png)

> Có một [phiên bản tương tác của bài viết này](https://trekhleb.dev/blog/2021/content-aware-image-resizing-in-javascript/) nơi bạn có thể tải lên và thay đổi kích thước hình ảnh tùy chỉnh của mình.

## Tóm Tắt

Đã có nhiều bài viết tuyệt vời viết về _Thuật toán Carving Seam_, nhưng tôi không thể kiềm chế được sự hứng thú để khám phá thuật toán thanh lịch, mạnh mẽ và _vẫn đơn giản_ này một cách riêng của mình, và viết về kinh nghiệm cá nhân của tôi với nó. Một điểm khác thu hút sự chú ý của tôi (như một người tạo ra [javascript-algorithms](https://github.com/trekhleb/javascript-algorithms)) là sự thật rằng phương pháp _Lập trình Động (DP)_ có thể được áp dụng một cách mượt mà để giải quyết nó. Và, nếu bạn giống như tôi và vẫn đang trên hành trình "học thuật toán" của mình, giải pháp thuật toán này có thể làm phong phú thêm bộ công cụ DP cá nhân của bạn.

Vì vậy, với bài viết này tôi muốn làm ba điều:

1. Cung cấp cho bạn một **công cụ thay đổi kích thước có ý thức về nội dung** tương tác để bạn có thể chơi với việc thay đổi kích thước hình ảnh của riêng bạn
2. Giải thích ý tưởng đằng sau **Thuật toán Carving Seam**
3. Giải thích phương pháp **lập trình động** để thực hiện thuật toán (chúng tôi sẽ sử dụng TypeScript cho nó)

### Thay Đổi Kích Thước Hình Ảnh Có Ý Thức Về Nội Dung

_Thay đổi kích thước hình ảnh có ý thức về nội dung_ có thể được áp dụng khi cần thay đổi tỷ lệ hình ảnh (tức là giảm chiều rộng trong khi giữ chiều cao) và khi việc mất một số phần của hình ảnh không mong muốn. Thực hiện việc co giãn hình ảnh một cách trực tiếp trong trường hợp này sẽ làm méo mó các đối tượng trong đó. Để bảo tồn tỷ lệ của các đối tượng trong khi thay đổi tỷ lệ hình ảnh, chúng ta có thể sử dụng [Thuật toán Carving Seam](https://perso.crans.org/frenoy/matlab2012/seamcarving.pdf) được giới thiệu bởi _Shai Avidan_ và _Ariel Shamir_.

Ví dụ dưới đây cho thấy cách chiều rộng hình ảnh gốc đã giảm đi 50% bằng cách sử dụng _thay đổi kích thước có ý thức về nội dung_ (hình ảnh bên trái) và _co giãn trực tiếp_ (hình ảnh bên phải). Trong trường hợp cụ thể này, hình ảnh bên trái trông tự nhiên hơn vì tỷ lệ của các quả bóng bay đã được bảo tồn.

![Thay Đổi Kích Thước Hình Ảnh Có Ý Thức Về Nội Dung](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/01-resizing-options.png)

Ý tưởng của thuật toán Carving Seam là tìm ra _đường cắt_ (chuỗi liên tục các điểm ảnh) có đóng góp thấp nhất vào nội dung hình ảnh và sau đó _chạm_ (xóa) nó đi. Quá trình này lặp lại điều này cho đến khi chúng ta có được chiều rộng hoặc chiều cao hình ảnh yêu cầu. Trong ví dụ dưới đây, bạn có thể thấy rằng các điểm ảnh của quả bóng bay nóng hơn nhiều so với các điểm ảnh của bầu trời. Do đó, các điểm ảnh của bầu trời được loại bỏ trước.

![JS IMAGE CARVER DEMO](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/10-demo-01.gif)

Tìm ra đường cắt có năng lượng thấp nhất là một nhiệm vụ tốn công suất tính toán (đặc biệt là đối với các hình ảnh lớn). Để làm cho việc tìm kiếm đường cắt nhanh hơn, phương pháp _lập trình động_ có thể được áp dụng (chúng tôi sẽ đi qua chi tiết triển khai bên dưới).

### Loại Bỏ Đối Tượng

Mức quan trọng của mỗi điểm ảnh (còn được gọi là năng lượng của điểm ảnh) được tính dựa trên sự khác biệt về màu sắc (`R`, `G`, `B`, `A`) giữa hai điểm ảnh kề nhau. Bây giờ, nếu chúng ta đặt năng lượng của điểm ảnh ở mức thấp thật sự (tức là bằng cách vẽ một mặt nạ lên đỉnh của chúng), thuật toán Carving Seam sẽ thực hiện việc **loại bỏ đối tượng** cho chúng ta một cách miễn phí.

![JS IMAGE CARVER OBJECT REMOVAL DEMO](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/10-demo-02.gif)

### Demo JS IMAGE CARVER

Tôi đã tạo ra ứng dụng web [JS IMAGE CARVER](https://trekhleb.dev/js-image-carver/) (và cũng [được công bố mở trên GitHub](https://github.com/trekhleb/js-image-carver)) mà bạn có thể sử dụng để chơi với việc thay đổi kích thước của hình ảnh tùy chỉnh của bạn.

### Thêm ví dụ

Dưới đây là một số ví dụ khác về cách thuật toán xử lý với các nền phức tạp hơn.

Núi trên nền đẹp được thu nhỏ mà không có đường cắt rõ ràng.

![Demo thay đổi kích thước với nền phức tạp hơn](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/11-demo-01.png)

Tương tự, với sóng biển. Thuật toán bảo tồn cấu trúc sóng mà không làm méo mó các vận động viên lướt sóng.

![Demo thay đổi kích thước với nền phức tạp hơn](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/11-demo-02.png)

Chúng ta cần nhớ rằng thuật toán Carving Seam không phải là một giải pháp toàn diện, và nó có thể không hoạt động cho việc thay đổi kích thước hình ảnh nơi _hầu hết các điểm ảnh là cạnh_ (trông quan trọng với thuật toán). Trong trường hợp này, nó bắt đầu làm méo mó cả các phần quan trọng của hình ảnh. Trong ví dụ dưới đây, việc thay đổi kích thước hình ảnh có ý thức về nội dung trông khá giống với một việc co giãn trực tiếp vì đối với thuật toán, tất cả các điểm ảnh đều trông quan trọng, và nó khó phân biệt được khuôn mặt của Van Gogh với nền.

![Ví dụ khi thuật toán không hoạt động như mong đợi](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/12-demo-01.png)

## Cách Thức Hoạt Động của Thuật Toán Carving Seam

Hãy tưởng tượng chúng ta có một bức ảnh kích thước `1000 x 500 px`, và chúng ta muốn thay đổi kích thước của nó thành `500 x 500 px` để biến nó thành hình vuông (hãy nói tỷ lệ hình vuông sẽ phù hợp hơn với dòng thời gian Instagram). Trong trường hợp này, chúng ta có thể muốn đặt một số **yêu cầu cho quá trình thay đổi kích thước** như sau:

- _Bảo tồn các phần quan trọng của hình ảnh_ (tức là nếu trước khi thay đổi kích thước có 5 cái cây thì chúng ta muốn có 5 cái cây sau khi thay đổi kích thước).
- _Bảo tồn tỷ lệ_ của các phần quan trọng của hình ảnh (tức là bánh xe xe hơi hình tròn không nên bị ép vào hình bánh xe hình ellipse)

Để tránh thay đổi các phần quan trọng của hình ảnh, chúng ta có thể tìm ra **chuỗi liên tục các điểm ảnh (đường cắt)**, đi từ trên xuống và có _đóng góp thấp nhất vào nội dung_ của hình ảnh (tránh các phần quan trọng) và sau đó loại bỏ nó. Việc loại bỏ đường cắt sẽ làm giảm kích thước của hình ảnh đi 1 điểm ảnh. Chúng ta sau đó lặp lại bước này cho đến khi hình ảnh có được chiều rộng mong muốn.

Câu hỏi là làm thế nào để xác định _sự quan trọng của điểm ảnh_ và đóng góp của nó vào nội dung (trong bài báo gốc, các tác giả sử dụng thuật ngữ **năng lượng của điểm ảnh**). Một trong những cách để làm điều này là coi tất cả các điểm ảnh tạo thành các cạnh là quan trọng. Trong trường hợp một điểm ảnh là một phần của cạnh, màu của nó sẽ có sự khác biệt lớn hơn giữa các điểm ảnh láng giềng (trái và phải) so với điểm ảnh không phải là một phần của cạnh.

![Sự khác biệt màu của các điểm ảnh](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/30-pixel-energy-comparison.png)

Giả sử rằng màu của một điểm ảnh được biểu diễn bởi _4_ số (`R` - đỏ, `G` - xanh lá cây, `B` - xanh lam, `A` - alpha), chúng ta có thể sử dụng công thức sau để tính sự khác biệt màu (năng lượng của điểm ảnh):

![Công thức năng lượng của điểm ảnh](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/20-energy-formula.png)

Trong đó:

- `mEnergy` - _Năng lượng_ (quan trọng) của điểm ảnh _giữa_ (`[0..626]` nếu làm tròn)
- `lR` - Giá trị kênh _đỏ_ cho điểm ảnh _trái_ (`[0..255]`)
- `mR` - Giá trị kênh _đỏ_ cho điểm ảnh _giữa_ (`[0..255]`)
- `rR` - Giá trị kênh _đỏ_ cho điểm ảnh _phải_ (`[0..255]`)
- `lG` - Giá trị kênh _xanh lá cây_ cho điểm ảnh _trái_ (`[0..255]`)
- và cetera...

Trong công thức trên, chúng ta không xem xét kênh alpha (độ trong suốt) tạm thời, giả định rằng không có điểm ảnh trong suốt trong hình ảnh. Sau này, chúng ta sẽ sử dụng kênh alpha để tạo mặt nạ và để loại bỏ đối tượng.

![Ví dụ về cách tính năng lượng của điểm ảnh](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/30-pixel-energy-calculation-example.png)

Bây giờ, khi chúng ta biết cách tìm ra năng lượng của một điểm ảnh, chúng ta có thể tính toán, cái gọi là, **bản đồ năng lượng** mà sẽ chứa các năng lượng của mỗi điểm ảnh của hình ảnh. Trên mỗi bước thay đổi kích thước, bản đồ năng lượng nên được tính toán lại (ít nhất là một phần, chi tiết hơn về điều này ở dưới) và sẽ có kích thước giống như hình ảnh.

Ví dụ, trên bước thay đổi kích thước đầu tiên, chúng ta sẽ có một hình ảnh `1000 x 500` và

một bản đồ năng lượng `1000 x 500`. Trên bước thay đổi kích thước thứ hai, chúng ta sẽ loại bỏ đường cắt từ hình ảnh và tính toán lại bản đồ năng lượng dựa trên hình ảnh đã bị co lại mới. Do đó, chúng ta sẽ có một hình ảnh `999 x 500` và một bản đồ năng lượng `999 x 500`.

Năng lượng càng cao của điểm ảnh thì khả năng cao hơn là nó là một phần của một cạnh, và nó quan trọng cho nội dung của hình ảnh và khả năng ít có khả năng rằng chúng ta cần phải loại bỏ nó.

Để minh họa bản đồ năng lượng, chúng ta có thể gán một màu sáng hơn cho các điểm ảnh có năng lượng cao hơn và màu tối cho các điểm ảnh có năng lượng thấp hơn. Dưới đây là một ví dụ giả mạo về cách bản đồ năng lượng có thể trông như thế nào. Bạn có thể thấy đường sáng đại diện cho cạnh và mà chúng ta muốn bảo tồn trong quá trình thay đổi kích thước.

![Phác thảo bản đồ năng lượng](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/30-energy-map-padding.png)

Dưới đây là một ví dụ thực về bản đồ năng lượng cho hình ảnh demo bạn đã thấy ở trên (với các quả bóng bay nóng).

![Ví dụ về bản đồ năng lượng](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/40-energy-map.png)

Bạn có thể chơi với các hình ảnh tùy chỉnh của mình và xem cách bản đồ năng lượng sẽ trông như thế nào trong [phiên bản tương tác của bài viết](https://trekhleb.dev/blog/2021/content-aware-image-resizing-in-javascript/).

Chúng ta có thể sử dụng bản đồ năng lượng để tìm ra các đường cắt (một sau một) có năng lượng thấp nhất và bằng cách này để quyết định những điểm ảnh nào cuối cùng nên bị xóa đi.

![Tìm kiếm đường cắt](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/41-seam-search.png)

Tìm kiếm đường cắt có năng lượng thấp nhất không phải là một nhiệm vụ dễ dàng và đòi hỏi phải khám phá nhiều kết hợp điểm ảnh có thể trước khi đưa ra quyết định. Chúng ta sẽ áp dụng phương pháp lập trình động để tăng tốc độ cho quá trình này.

Trong ví dụ dưới đây, bạn có thể thấy bản đồ năng lượng với đường cắt năng lượng thấp nhất đầu tiên đã được tìm thấy cho nó.

![Ví dụ về bản đồ năng lượng với đường cắt](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/40-energy-map-with-seam.png)

Trong các ví dụ trên, chúng ta đã giảm chiều rộng của hình ảnh. Một phương pháp tương tự có thể được sử dụng để giảm chiều cao của hình ảnh. Tuy nhiên, chúng ta cần "xoay" phương pháp:

- bắt đầu sử dụng điểm ảnh láng giềng _trên_ và _dưới_ (thay vì các điểm ảnh _trái_ và _phải_) để tính năng lượng của điểm ảnh
- khi tìm kiếm đường cắt, chúng ta cần di chuyển từ _trái_ sang _phải_ (thay vì từ _trên_ xuống _dưới_)

## Cài đặt trong TypeScript

> Bạn có thể tìm mã nguồn và các hàm được đề cập dưới đây trong kho lưu trữ [js-image-carver](https://github.com/trekhleb/js-image-carver).

Để triển khai thuật toán, chúng tôi sẽ sử dụng TypeScript. Nếu bạn muốn một phiên bản JavaScript, bạn có thể bỏ qua (xóa) các định nghĩa loại và việc sử dụng chúng.

Vì lý do đơn giản, hãy triển khai thuật toán chỉ cho việc giảm _chiều rộng_ của hình ảnh.

### Thay đổi kích thước chiều rộng dựa trên nội dung (hàm nhập)

Đầu tiên, hãy xác định một số loại thông thường mà chúng ta sẽ sử dụng trong quá trình triển khai thuật toán.

```typescript
// Loại mô tả kích thước hình ảnh (chiều rộng và chiều cao).
type ImageSize = { w: number; h: number };

// Tọa độ của điểm ảnh.
type Coordinate = { x: number; y: number };

// Đường cắt là một chuỗi liên tục của điểm ảnh (tọa độ).
type Seam = Coordinate[];

// Bản đồ năng lượng là một mảng 2D có cùng chiều rộng và chiều cao
// như hình ảnh mà bản đồ này đang được tính toán cho.
type EnergyMap = number[][];

// Loại mô tả màu RGBA của điểm ảnh.
type Color =
  | [
      r: number, // Đỏ
      g: number, // Xanh lá cây
      b: number, // Xanh dương
      a: number // Alpha (độ trong suốt)
    ]
  | Uint8ClampedArray;
```

Ở mức cao hơn, thuật toán bao gồm các bước sau:

1. Tính toán **bản đồ năng lượng** cho phiên bản hiện tại của hình ảnh.
2. Tìm **đường cắt** có năng lượng thấp nhất dựa trên bản đồ năng lượng (đây là nơi chúng tôi sẽ áp dụng Lập trình Động).
3. **Xóa đường cắt** có đường cắt có năng lượng thấp nhất khỏi hình ảnh.
4. **Lặp lại** cho đến khi chiều rộng của hình ảnh được giảm xuống giá trị mong muốn.

```typescript
type ResizeImageWidthArgs = {
  img: ImageData; // Dữ liệu hình ảnh chúng ta muốn thay đổi kích thước.
  toWidth: number; // Chiều rộng cuối cùng mà chúng ta muốn hình ảnh co lại.
};

type ResizeImageWidthResult = {
  img: ImageData; // Dữ liệu hình ảnh đã thay đổi kích thước.
  size: ImageSize; // Kích thước hình ảnh đã thay đổi (w x h).
};

// Thực hiện việc thay đổi kích thước chiều rộng hình ảnh dựa trên nội dung sử dụng phương pháp seam carving.
export const resizeImageWidth = ({
  img,
  toWidth,
}: ResizeImageWidthArgs): ResizeImageWidthResult => {
  // Vì lý do hiệu suất, chúng ta muốn tránh việc thay đổi kích thước mảng dữ liệu hình ảnh.
  // Thay vào đó, chúng ta chỉ giữ bản ghi về chiều rộng và chiều cao của hình ảnh đã thay đổi.
  const size: ImageSize = { w: img.width, h: img.height };

  // Tính toán số điểm ảnh cần xóa.
  const pxToRemove = img.width - toWidth;
  if (pxToRemove < 0) {
    throw new Error('Không hỗ trợ phương pháp phóng to cho tới bây giờ');
  }

  let energyMap: EnergyMap | null = null;
  let seam: Seam | null = null;

  // Xóa các đường cắt có năng lượng thấp nhất một cách tuần tự.
  for (let i = 0; i < pxToRemove; i += 1) {
    // 1. Tính toán bản đồ năng lượng cho phiên bản hiện tại của hình ảnh.
    energyMap = calculateEnergyMap(img, size);
    //

2. Tìm đường cắt có năng lượng thấp nhất dựa trên bản đồ năng lượng.
    seam = findLowEnergySeam(energyMap, size);

    // 3. Xóa đường cắt có đường cắt có năng lượng thấp nhất từ hình ảnh.
    deleteSeam(img, seam, size);

    // Giảm chiều rộng của hình ảnh và tiếp tục các lần lặp.
    size.w -= 1;
  }

  // Trả về hình ảnh đã thay đổi kích thước và kích thước cuối cùng của nó.
  // Dữ liệu hình ảnh thực tế là một tham chiếu đến ImageData, vì vậy kỹ thuật
  // người gọi của hàm đã có con trỏ này. Nhưng hãy vẫn trả về nó để đọc mã dễ hiểu hơn.
  return { img, size };
};
```

Hình ảnh cần được thay đổi kích thước được chuyển đến hàm dưới dạng [ImageData](https://developer.mozilla.org/en-US/docs/Web/API/ImageData). Bạn có thể vẽ hình ảnh lên canvas và sau đó trích xuất ImageData từ canvas như sau:

```javascript
const ctx = canvas.getContext('2d');
const imgData = ctx.getImageData(0, 0, imgWidth, imgHeight);
```

> Cách tải lên và vẽ hình ảnh trong JavaScript nằm ngoài phạm vi của bài viết này, nhưng bạn có thể tìm mã nguồn đầy đủ về cách thực hiện điều này bằng React trong kho lưu trữ [js-image-carver](https://github.com/trekhleb/js-image-carver).

Hãy phân rã từng bước một và triển khai các hàm `calculateEnergyMap()`, `findLowEnergySeam()` và `deleteSeam()`.

### Tính năng lượng của điểm ảnh

Ở đây, chúng ta áp dụng công thức khác biệt màu sắc đã mô tả ở trên. Đối với các biên trái và phải (khi không có hàng xóm bên trái hoặc bên phải), chúng ta bỏ qua hàng xóm và không tính chúng vào trong quá trình tính toán năng lượng.

```typescript
// Tính toán năng lượng của một điểm ảnh.
const getPixelEnergy = (
  left: Color | null,
  middle: Color,
  right: Color | null
): number => {
  // Điểm ảnh ở giữa là điểm ảnh mà chúng tôi đang tính toán năng lượng cho.
  const [mR, mG, mB] = middle;

  // Năng lượng từ điểm ảnh bên trái (nếu tồn tại).
  let lEnergy = 0;
  if (left) {
    const [lR, lG, lB] = left;
    lEnergy = (lR - mR) ** 2 + (lG - mG) ** 2 + (lB - mB) ** 2;
  }

  // Năng lượng từ điểm ảnh bên phải (nếu tồn tại).
  let rEnergy = 0;
  if (right) {
    const [rR, rG, rB] = right;
    rEnergy = (rR - mR) ** 2 + (rG - mG) ** 2 + (rB - mB) ** 2;
  }

  // Năng lượng của điểm ảnh kết quả.
  return Math.sqrt(lEnergy + rEnergy);
};
```

### Tính toán bản đồ năng lượng

Hình ảnh mà chúng ta đang làm việc có định dạng [ImageData](https://developer.mozilla.org/en-US/docs/Web/API/ImageData). Điều này có nghĩa là tất cả các điểm ảnh (và màu sắc của chúng) được lưu trữ trong một mảng _1D_ [Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray). Vì mục đích đọc mã dễ hiểu hơn, hãy giới thiệu một cặp hàm trợ giúp để cho phép chúng ta làm việc với mảng Uint8ClampedArray như một ma trận _2D_ thay vì như một mảng _1D_.

```typescript
// Hàm trợ giúp trả về màu sắc của điểm ảnh.
const getPixel = (img: ImageData, { x, y }: Coordinate): Color => {
  // Mảng dữ liệu ImageData là một mảng 1D phẳng.
  // Do đó, chúng ta cần chuyển đổi các tọa độ x và y thành chỉ số tuyến tính.
  const i = y * img.width + x;
  const cellsPerColor = 4; // RGBA
  // Để hiệu quả hơn, thay vì tạo một mảng con mới, chúng tôi trả về
  // một con trỏ đến phần của mảng ImageData.
  return img.data.subarray(
    i * cellsPerColor,
    i * cellsPerColor + cellsPerColor
  );
};

// Hàm trợ giúp thiết lập màu sắc của điểm ảnh.
const setPixel = (img: ImageData, { x, y }: Coordinate, color: Color): void => {
  // Mảng dữ liệu ImageData là một mảng 1D phẳng.
  // Do đó, chúng ta cần chuyển đổi các tọa độ x và y thành chỉ số tuyến tính.
  const i = y * img.width + x;
  const cellsPerColor = 4; // RGBA
  img.data.set(color, i * cellsPerColor);
};
```

Để tính toán bản đồ năng lượng, chúng ta duyệt qua từng điểm ảnh của hình ảnh và gọi hàm `getPixelEnergy()` đã mô tả trước đó.

```typescript
// Hàm trợ giúp tạo ma trận (mảng 2D) có kích thước cụ thể
// (w x h) và điền nó bằng giá trị đã cho.
const matrix = <T>(w: number, h: number, filler: T): T[][] => {
  return new Array(h).fill(null).map(() => {
    return new Array(w).fill(filler);
  });
};

// Tính toán năng lượng của mỗi điểm ảnh của hình ảnh.
const calculateEnergyMap = (img: ImageData, { w, h }: ImageSize): EnergyMap => {
  // Tạo một bản đồ năng lượng trống nơi mỗi điểm ảnh có năng lượng vô cùng cao.
  // Chúng tôi sẽ cập nhật năng lượng của mỗi điểm ảnh.
  const energyMap: number[][] = matrix<number>(w, h, Infinity);
  for (let y = 0; y < h; y += 1) {
    for (let x = 0; x < w; x += 1) {
      // Điểm ảnh bên trái có thể không tồn tại nếu chúng tôi đang ở biên trái cực của hình ảnh.
      const left = x - 1 >= 0 ? getPixel(img, { x: x - 1, y }) : null;
      // Màu sắc của điểm ảnh ở giữa mà chúng tôi đang tính toán năng lượng cho.
      const middle = getPixel(img, { x, y });
      // Điểm ảnh bên phải có thể không tồn tại nếu chúng tôi đang ở biên phải cực

 của hình ảnh.
      const right = x + 1 < w ? getPixel(img, { x: x + 1, y }) : null;
      energyMap[y][x] = getPixelEnergy(left, middle, right);
    }
  }
  return energyMap;
};
```

> Bản đồ năng lượng sẽ được tính toán lại sau mỗi lần thay đổi kích thước. Điều này có nghĩa là nó sẽ được tính toán lại, chẳng hạn, 500 lần nếu chúng ta cần thu nhỏ hình ảnh đi 500 điểm ảnh, điều này không hiệu quả. Để tăng tốc độ tính toán của bản đồ năng lượng ở các bước 2, 3 và các bước tiếp theo, chúng ta có thể tính toán lại năng lượng chỉ cho những điểm ảnh được đặt xung quanh đường cắt sẽ được loại bỏ. Vì lý do đơn giản, tối ưu hóa này đã bị bỏ qua ở đây, nhưng bạn có thể tìm mã nguồn ví dụ trong kho lưu trữ [js-image-carver](https://github.com/trekhleb/js-image-carver).

### Tìm đường cắt có năng lượng thấp nhất (phương pháp lập trình động)

> Tôi đã mô tả một số kiến thức cơ bản về lập trình động trong bài viết [Dynamic Programming vs Divide-and-Conquer](https://trekhleb.dev/blog/2018/dynamic-programming-vs-divide-and-conquer/). Có một ví dụ về lập trình động dựa trên vấn đề khoảng cách chỉnh sửa tối thiểu. Bạn có thể muốn kiểm tra để hiểu rõ hơn về ngữ cảnh.

Vấn đề chúng ta cần giải quyết bây giờ là tìm đường (đường cắt) trên bản đồ năng lượng đi từ trên xuống dưới và có tổng năng lượng pixel nhỏ nhất.

#### Phương pháp ngây thơ

Phương pháp ngây thơ sẽ là kiểm tra tất cả các đường đi có thể một sau một.

![Phương pháp ngây thơ](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/50-naive-approach.png)

Đi từ trên xuống dưới, cho mỗi điểm ảnh, chúng ta có 3 lựa chọn (↙︎ đi xuống bên trái, ↓ đi xuống, ↘︎ đi xuống bên phải). Điều này cho chúng ta độ phức tạp thời gian là `O(w * 3^h)` hoặc đơn giản là `O(3^h)`, trong đó `w` và `h` lần lượt là chiều rộng và chiều cao của hình ảnh. Phương pháp này trông chậm.

#### Phương pháp tham lam

Chúng ta cũng có thể thử chọn điểm ảnh tiếp theo là điểm ảnh có năng lượng thấp nhất, hy vọng rằng năng lượng của đường cắt kết quả sẽ là nhỏ nhất.

![Phương pháp tham lam](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/51-greedy-approach.png)

Phương pháp này không cho kết quả tồi nhất, nhưng không thể đảm bảo rằng chúng ta sẽ tìm được giải pháp tốt nhất có sẵn. Trên hình ảnh trên, bạn có thể thấy cách phương pháp tham lam đã chọn `5` thay vì `10` ban đầu và bỏ lỡ chuỗi điểm ảnh tối ưu.

Phần tốt của phương pháp này là nó nhanh chóng, và nó có độ phức tạp thời gian là `O(w + h)`, trong đó `w` và `h` lần lượt là chiều rộng và chiều cao của hình ảnh. Trong trường hợp này, chi phí của tốc độ là chất lượng thấp của việc thay đổi kích thước. Chúng ta cần tìm một giá trị nhỏ nhất trong hàng đầu tiên (duyệt `w` ô) và sau đó chúng ta khám phá chỉ 3 ô hàng xóm cho mỗi hàng (duyệt `h` hàng).

#### Phương pháp lập trình động

Bạn có thể đã nhận ra rằng trong phương pháp ngây thơ chúng ta đã tính tổng năng lượng pixel giống nhau lần lượt khi tính toán năng lượng của các đường cắt kết quả.

![Các vấn đề lặp lại](https://raw.githubusercontent.com/trekhleb/trekhleb

.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/52-dp-repeated-problems.png)

Trong ví dụ trên, bạn thấy rằng cho hai đường cắt đầu tiên, chúng ta đang sử dụng lại năng lượng của đường cắt ngắn hơn (có năng lượng là `235`). Thay vì thực hiện một thao tác `235 + 70` để tính toán năng lượng của đường cắt thứ hai, chúng ta đang thực hiện bốn thao tác `(5 + 0 + 80 + 150) + 70`.

> Sự thật rằng chúng ta đang sử dụng lại năng lượng của đường cắt trước để tính toán năng lượng của đường cắt hiện tại có thể được áp dụng đệ quy cho tất cả các đường cắt ngắn hơn lên tới đường cắt đầu tiên ở hàng 1. Khi chúng ta có các bài toán con trùng lặp như vậy, [đó là một dấu hiệu](https://trekhleb.dev/blog/2018/dynamic-programming-vs-divide-and-conquer/) cho thấy vấn đề chung _có thể_ được tối ưu hóa bằng cách tiế approach này.

Vì vậy, chúng ta có thể **lưu năng lượng của đường cắt hiện tại** tại pixel cụ thể trong một bảng bổ sung `seamsEnergies` để làm cho nó có thể sử dụng lại cho việc tính toán các đường cắt tiếp theo nhanh hơn (bảng `seamsEnergies` sẽ có kích thước giống như bản đồ năng lượng và hình ảnh chính nó).

Hãy cũng nhớ rằng cho một pixel cụ thể trên hình ảnh (ví dụ: ở góc dưới bên trái) chúng ta có thể có _nhiều_ giá trị của năng lượng đường cắt trước đó.

![Chọn đường cắt nào](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/53-dp-what-to-choose.png)

Vì chúng ta đang tìm kiếm một đường cắt có năng lượng kết quả thấp nhất nên sẽ hợp lý khi chọn đường cắt trước đó có năng lượng kết quả thấp nhất.

![Ví dụ về năng lượng đường cắt](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/56-dp-seams-energies-example.png)

Nói chung, chúng ta có ba đường cắt trước đó có thể lựa chọn:

![Ba lựa chọn để chọn](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/55-dp-three-options.png)

Bạn có thể nghĩ về nó như sau:

- Ô `[1][x]`: chứa năng lượng thấp nhất có thể của đường cắt bắt đầu từ đâu đó trên hàng `[0][?]` và kết thúc tại ô `[1][x]`
- **Ô hiện tại** `[2][3]`: chứa năng lượng thấp nhất có thể của đường cắt bắt đầu từ đâu đó trên hàng `[0][?]` và kết thúc tại ô `[2][3]`. Để tính toán nó, chúng ta cần cộng năng lượng của pixel hiện tại `[2][3]` (từ bản đồ năng lượng) với `min(seam_energy_1_2, seam_energy_1_3, seam_energy_1_4)`

Nếu chúng ta điền đầy đủ bảng `seamsEnergies`, thì số nhỏ nhất ở hàng dưới cùng sẽ là năng lượng đường cắt nhỏ nhất có thể.

Hãy thử điền vài ô của bảng này để xem nó hoạt động như thế nào.

![Điều hướng bản đồ năng lượng đường cắt](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/57-dp-seams-energies-traversal.png)

Sau khi điền bảng `seamsEnergies`, chúng ta có thể thấy rằng pixel năng lượng thấp nhất có năng lượng là `50`. Để thuận tiện trong quá trình tạo bảng `seamsEnergies` cho mỗi pixel, chúng ta có thể lưu không chỉ năng lượng của đường cắt mà còn là tọa độ của đường cắt trước đó. Điều này sẽ cho chúng ta khả năng tái tạo đường cắt từ dưới lên trên một cách dễ dàng.

Độ phức tạp thời gian của phương pháp lập trình động sẽ là `O(w * h)`, trong đó `w` và `h` lần lượt là chiều rộng và chiều cao của hình ảnh. Chúng ta cần tính năng lượng cho _mỗi_ pixel của hình ảnh.

Dưới đây là một ví dụ về cách triển khai logic này:

```typescript
// Thông tin về các pixel

 trong đường cắt.
type SeamPixelMeta = {
  energy: number; // Năng lượng của pixel.
  coordinate: Coordinate; // Tọa độ của pixel.
  previous: Coordinate | null; // Pixel trước đó trong một đường cắt.
};

// Tìm đường cắt (dãy các pixel từ trên xuống dưới) có
// năng lượng kết quả thấp nhất sử dụng phương pháp lập trình động.
const findLowEnergySeam = (energyMap: EnergyMap, { w, h }: ImageSize): Seam => {
  // Mảng 2D có kích thước w và h, mỗi pixel chứa
  // thông tin metadata của đường cắt (năng lượng pixel, tọa độ pixel và pixel trước
  // đó từ đường cắt năng lượng thấp nhất ở điểm này).
  const seamsEnergies: (SeamPixelMeta | null)[][] =
    matrix<SeamPixelMeta | null>(w, h, null);

  // Điền vào hàng đầu tiên của bảng bằng cách sao chép năng lượng
  // từ bản đồ năng lượng.
  for (let x = 0; x < w; x += 1) {
    const y = 0;
    seamsEnergies[y][x] = {
      energy: energyMap[y][x],
      coordinate: { x, y },
      previous: null,
    };
  }

  // Điền vào phần còn lại của các hàng.
  for (let y = 1; y < h; y += 1) {
    for (let x = 0; x < w; x += 1) {
      // Tìm ô kề trên với năng lượng thấp nhất.
      // Ô này sẽ là đuôi của một đường cắt với năng lượng thấp nhất tại điểm này.
      // Điều này không có nghĩa là đường cắt (đường dẫn) này có năng lượng thấp nhất
      // toàn cầu. Thay vào đó, điều này có nghĩa là chúng ta đã tìm thấy một đường dẫn với
      // năng lượng thấp nhất có thể dẫn chúng ta đến pixel hiện tại với tọa độ x và y.
      let minPrevEnergy = Infinity;
      let minPrevX: number = x;
      for (let i = x - 1; i <= x + 1; i += 1) {
        if (i >= 0 && i < w && seamsEnergies[y - 1][i].energy < minPrevEnergy) {
          minPrevEnergy = seamsEnergies[y - 1][i].energy;
          minPrevX = i;
        }
      }

      // Cập nhật ô hiện tại.
      seamsEnergies[y][x] = {
        energy: minPrevEnergy + energyMap[y][x],
        coordinate: { x, y },
        previous: { x: minPrevX, y: y - 1 },
      };
    }
  }

  // Tìm nơi đường cắt năng lượng thấp nhất kết thúc.
  // Chúng ta cần tìm đuôi của đường cắt năng lượng thấp nhất để bắt đầu
  // điều hướng nó từ đuôi đến đầu (từ dưới lên trên).
  let lastMinCoordinate: Coordinate | null = null;
  let minSeamEnergy = Infinity;
  for (let x = 0; x < w; x += 1) {
    const y = h - 1;
    if (seamsEnergies[y][x].energy < minSeamEnergy) {
      minSeamEnergy = seamsEnergies[y][x].energy;
      lastMinCoordinate = { x, y };
    }
  }

  // Tìm đường cắt năng lượng thấp nhất.
  // Khi chúng ta biết nơi đuôi đặt, chúng ta có thể điều hướng và lắp ráp
  // đường cắt năng lượng thấp nhất dựa trên giá trị "trước" của metadata pixel đường cắt.
  const seam: Seam = [];
  if (!lastMinCoordinate) {
    return seam;
  }

  const { x: lastMinX, y: lastMinY } = lastMinCoordinate;

  // Thêm pixel mới vào đường cắt một cách tuần tự cho đến khi chúng ta đến đầu.
  let currentSeam = seamsEnergies[lastMinY][lastMinX];
  while (currentSeam) {
    seam.push(currentSeam.coordinate);
    const prevMinCoordinates = currentSeam.previous;
    if (!prevMinCoordinates) {
      currentSeam = null;
    } else {
      const { x: prevMinX, y: prevMinY } = prevMinCoordinates;
      currentSeam = seamsEnergies[prevMinY][prevMinX];
    }
  }

  return seam;
};
```

### Xóa đường cắt có năng lượng thấp nhất

Sau khi chúng ta đã tìm ra đường cắt có năng lượng thấp nhất, chúng ta cần xóa (điêu chỉnh) các pixel tạo thành nó khỏi hình ảnh. Việc xóa diễn ra bằng cách dịch chuyển các pixel sang phải của đường cắt sang trái `1px`. Vì lý do hiệu suất, chúng ta không thực sự xóa các cột cuối cùng. Thay vào đó, thành phần hiển thị sẽ chỉ bỏ qua phần của hình ảnh nằm ngoài chiều rộng của hình ảnh đã được thay đổi kích thước.

![Xóa đường cắt](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/60-deleting-example.png)

```typescript
// Xóa đường cắt khỏi dữ liệu hình ảnh.
// Chúng ta xóa pixel trong mỗi hàng và sau đó dịch chuyển các pixel còn lại của hàng sang trái.
const deleteSeam = (img: ImageData, seam: Seam, { w }: ImageSize): void => {
  seam.forEach(({ x: seamX, y: seamY }: Coordinate) => {
    for (let x = seamX; x < w - 1; x += 1) {
      const nextPixel = getPixel(img, { x: x + 1, y: seamY });
      setPixel(img, { x, y: seamY }, nextPixel);
    }
  });
};
```

## Xóa đối tượng

Thuật toán Seam Carving cố gắng xóa các đường cắt được tạo thành từ các pixel có năng lượng thấp trước tiên. Chúng ta có thể tận dụng sự thật này và bằng cách gán năng lượng thấp cho một số pixel một cách thủ công (tức là bằng cách vẽ trên hình ảnh và che khuất một số khu vực của nó), chúng ta có thể làm cho thuật toán Seam Carving thực hiện _xóa đối tượng_ cho chúng ta miễn phí.

Hiện tại, trong hàm `getPixelEnergy()`, chúng ta chỉ sử dụng các kênh màu `R`, `G`, `B` để tính toán năng lượng của pixel. Nhưng cũng có tham số `A` (alpha, độ trong suốt) của màu mà chúng ta chưa sử dụng. Chúng ta có thể sử dụng kênh độ trong suốt để thông báo cho thuật toán rằng các pixel trong suốt là các pixel chúng ta muốn xóa. Bạn có thể kiểm tra [mã nguồn của hàm năng lượng](https://github.com/trekhleb/js-image-carver/blob/main/src/utils/contentAwareResizer.ts#L54) mà tính đến độ trong suốt.

Dưới đây là cách thuật toán hoạt động cho việc xóa đối tượng.

![JS IMAGE CARVER OBJECT REMOVAL DEMO](https://raw.githubusercontent.com/trekhleb/trekhleb.github.io/master/src/posts/2021/content-aware-image-resizing-in-javascript/assets/10-demo-02.gif)

## Vấn đề và những gì tiếp theo

Ứng dụng web [JS IMAGE CARVER](https://github.com/trekhleb/js-image-carver) chắc chắn chưa thể trở thành một công cụ thay đổi kích thước sẵn sàng cho sản xuất. Mục đích chính của nó là thử nghiệm với thuật toán Seam Carving theo cách tương tác. Vì vậy, kế hoạch cho tương lai là tiếp tục thử nghiệm.

[Bài báo gốc](https://perso.crans.org/frenoy/matlab2012/seamcarving.pdf) mô tả cách thuật toán Seam Carving có thể được sử dụng không chỉ để co giảm kích thước mà còn để **mở rộng kích thước của hình ảnh**. Việc mở rộng, lần lượt, có thể được sử dụng để **mở rộng lại hình ảnh về chiều rộng ban đầu sau khi loại bỏ các đối tượng**.

Một lĩnh vực thử nghiệm thú vị khác có thể là làm cho thuật toán hoạt động **trực tiếp**.

> Đó là các kế hoạch cho tương lai, nhưng hiện tại, tôi hy vọng rằng ví dụ về việc giảm kích thước hình ảnh đã làm bạn thấy thú vị và hữu ích. Tôi cũng hy vọng rằng bạn đã hiểu được cách sử dụng lập trình động để triển khai nó.
>
> Vì vậy, chúc bạn may mắn với các thử nghiệm của riêng bạn!
