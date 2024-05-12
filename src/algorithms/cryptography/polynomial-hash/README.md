# Băm Đa Thức Cuộn

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

## Hàm Băm

**Hàm băm** được sử dụng để ánh xạ các tập dữ liệu lớn các phần tử có chiều dài tùy ý (_các khóa_) thành các tập dữ liệu nhỏ hơn các phần tử có chiều dài cố định (_các dấu vân tay_).

Ứng dụng cơ bản của băm là kiểm tra hiệu quả sự bằng nhau của các khóa bằng cách so sánh các dấu vân tay của chúng.

Một _xung đột_ xảy ra khi hai khóa khác nhau có cùng một dấu vân tay. Cách xử lý các xung đột là rất quan trọng trong hầu hết các ứng dụng của băm. Băm đặc biệt hữu ích trong việc xây dựng các thuật toán thực tiễn hiệu quả.

## Băm Cuộn

**Băm cuộn** (còn được gọi là băm đệ quy hoặc checksum cuộn) là một hàm băm nơi đầu vào được băm trong một cửa sổ di chuyển qua đầu vào.

Một số hàm băm cho phép băm cuộn được tính toán rất nhanh — giá trị băm mới được tính nhanh chóng chỉ với dữ liệu sau:

- giá trị băm cũ,
- giá trị cũ được loại bỏ khỏi cửa sổ,
- và giá trị mới được thêm vào cửa sổ.

## Băm Chuỗi Đa Thức

Một hàm băm lý tưởng cho chuỗi nên phụ thuộc vào cả _multiset_ của các ký tự có trong khóa và _thứ tự_ của các ký tự. Họ hàm băm phổ biến nhất xử lý các ký tự của một chuỗi như các hệ số của một _đa thức_ với biến số nguyên `p` và tính giá trị của nó theo mô-đun hằng số nguyên `M`:

_Thuật toán tìm kiếm chuỗi Rabin–Karp_ thường được giải thích sử dụng một hàm băm cuộn rất đơn giản chỉ sử dụng phép nhân và phép cộng — **băm đa thức cuộn**:

> H(s<sub>0</sub>, s<sub>1</sub>, ..., s<sub>k</sub>) = s<sub>0</sub> _ p<sup>k-1</sup> + s<sub>1</sub> _ p<sup>k-2</sup> + ... + s<sub>k</sub> \* p<sup>0</sup>

trong đó `p` là hằng số, và _(s<sub>1</sub>, ..., s<sub>k</sub>)_ là các ký tự đầu vào.

Ví dụ, chúng ta có thể chuyển đổi chuỗi ngắn thành số khóa bằng cách nhân các mã số ký tự với lũy thừa của một hằng số. Từ ba chữ cái `ace` có thể được chuyển thành một số bằng cách tính:

> khóa = 1 _ 26<sup>2</sup> + 3 _ 26<sup>1</sup> + 5 \* 26<sup>0</sup>

Để tránh xử lý các giá trị `H` quá lớn, tất cả các phép toán đều được thực hiện theo mô-đun `M`.

> H(s<sub>0</sub>, s<sub>1</sub>, ..., s<sub>k</sub>) = (s<sub>0</sub> _ p<sup>k-1</sup> + s<sub>1</sub> _ p<sup>k-2</sup> + ... + s<sub>k</sub> \* p<sup>0</sup>) mod M

Việc lựa chọn cẩn thận các tham số `M`, `p` là quan trọng để có được các thuộc tính "tốt" của hàm băm, tức là tỷ lệ xung đột thấp.

Cách tiếp cận này có đặc điểm mong muốn là liên quan đến tất cả các ký tự trong chuỗi đầu vào. Giá trị khóa tính toán sau đó có thể được băm thành chỉ số mảng theo cách thông thường:

```javascript
function hash(key, arraySize) {
  const base = 13;

  let hash = 0;
  for (let charIndex = 0; charIndex < key.length; charIndex += 1) {
    const charCode = key.charCodeAt(charIndex);
    hash += charCode * base ** (key.length - charIndex - 1);
  }

  return hash % arraySize;
}
```

Phương thức `hash()` không hiệu quả như nó có thể. Ngoài việc chuyển đổi ký tự, có hai phép nhân và một phép cộng bên trong vòng lặp. Chúng ta có thể loại bỏ một phép nhân bằng cách sử dụng **phương pháp Horner**:

> a<sub>4</sub> _ x<sup>4</sup> + a<sub>3</sub> _ x<sup>3</sup> + a<sub>2</sub> _ x<sup>2</sup> + a<sub>1</sub> _ x<sup>1</sup> + a<sub>0</sub> = (((a<sub>4</sub> _ x + a<sub>3</sub>) _ x + a<sub>2</sub>) _ x + a<sub>1</sub>) _ x + a<sub>0</sub>

Nói cách khác:

> H<sub>i</sub> = (P \* H<sub>i-1</sub> + S<sub>i</sub>) mod M

Phương thức `hash()` không thể xử lý chuỗi dài vì hashVal vượt quá kích thước của int. Lưu ý rằng khóa luôn nhỏ hơn kích thước mảng. Trong phương pháp Horner, chúng ta có thể áp dụng toán tử modulo (%) tại mỗi bước trong tính toán. Điều này cho kết quả giống như áp dụng toán tử modulo một lần ở cuối, nhưng tránh được tràn số.

```javascript
function hash(key, arraySize) {
  const base = 13;

  let hash = 0;
  for (let charIndex = 0; charIndex < key.length; charIndex += 1) {
    const charCode = key.charCodeAt(charIndex);
    hash = (hash * base + charCode) % arraySize;
  }

  return hash;
}
```

Băm đa thức có một tính năng cuộn: các dấu vân tay có thể được cập nhật hiệu quả khi các ký tự được thêm vào hoặc loại bỏ ở các đầu của chuỗi (miễn là một mảng của các lũy thừa của p modulo M có độ dài đủ được lưu trữ). Thuật toán tìm kiếm mẫu Rabin–Karp phổ biến dựa trên tính năng này.

## Tài liệu tham khảo

- [Nơi sử dụng Băm Chuỗi Đa Thức](https://www.mii.lt/olympiads_in_informatics/pdf/INFOL119.pdf)
- [Băm trên uTexas](https://www.cs.utexas.edu/~mitra/csSpring2017/cs313/lectures/hash.html)
- [Hàm Băm trên Wikipedia](https://en.wikipedia.org/wiki/Hash_function)
- [Băm Cuộn trên Wikipedia](https://en.wikipedia.org/wiki/Rolling_hash)
