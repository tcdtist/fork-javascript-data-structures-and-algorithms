# Bit Manipulation

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

#### Lấy Bit

Phương thức này dịch chuyển bit liên quan đến vị trí số 0.
Sau đó, chúng ta thực hiện phép `AND` với số một có dạng bit
như `0001`. Điều này xóa tất cả các bit từ số gốc
ngoại trừ bit liên quan. Nếu bit liên quan là một,
kết quả là `1`, nếu không, kết quả là `0`.

> Xem [getBit.js](getBit.js) để biết thêm chi tiết.

#### Đặt Bit

Phương thức này dịch `1` qua `bitPosition` bit, tạo ra một
giá trị có dạng `00100`. Sau đó, chúng ta thực hiện phép `OR`
đặt bit cụ thể thành `1` nhưng không ảnh hưởng đến
các bit khác của số.

> Xem [setBit.js](setBit.js) để biết thêm chi tiết.

#### Xóa Bit

Phương thức này dịch `1` qua `bitPosition` bit, tạo ra một
giá trị có dạng `00100`. Sau đó, nó đảo ngược mặt nạ này để có được
số giống như `11011`. Sau đó, phép `AND` được áp dụng
với cả số và mặt nạ. Phép toán này loại bỏ bit đó.

> Xem [clearBit.js](clearBit.js) để biết thêm chi tiết.

#### Cập Nhật Bit

Phương thức này là sự kết hợp của các phương thức "Xóa Bit" và "Đặt Bit".

> Xem [updateBit.js](updateBit.js) để biết thêm chi tiết.

#### isEven

Phương thức này xác định xem số được cung cấp có là số chẵn không.
Nó dựa trên sự thật rằng số lẻ có bit cuối cùng ở phải cùng được thiết lập thành 1.

```text
Số: 5 = 0b0101
isEven: false

Số: 4 = 0b0100
isEven: true
```

> Xem [isEven.js](isEven.js) để biết thêm chi tiết.

#### isPositive

Phương thức này xác định xem số có là số dương không. Nó dựa trên sự thật rằng tất cả
các số dương có bit đầu tiên bên trái được thiết lập thành `0`. Tuy nhiên, nếu số được cung cấp là không
hoặc số không âm, nó vẫn nên trả về `false`.

```text
Số: 1 = 0b0001
isPositive: true

Số: -1 = -0b0001
isPositive: false
```

> Xem [isPositive.js](isPositive.js) để biết thêm chi tiết.

#### Nhân Lên Hai

Phương thức này dịch số gốc một bit sang trái.
Do đó, tất cả các thành phần số nhị phân (lũy thừa của hai) đều
được nhân lên hai và do đó chính số đó được
nhân lên hai.

```
Trước khi dịch
Số: 0b0101 = 5
Lũy thừa của hai: 0 + 2^2 + 0 + 2^0

Sau khi dịch
Số: 0b1010 = 10
Lũy thừa của hai: 2^3 + 0 + 2^1 + 0
```

> Xem [multiplyByTwo.js](multiplyByTwo.js) để biết thêm chi tiết.

#### Chia Cho Hai

Phương thức này dịch số gốc một bit sang phải.
Do đó, tất cả các thành phần số nhị phân (lũy thừa của hai) đều
bị chia cho hai và do đó chính số đó được
chia cho hai mà không có dư.

```
Trước khi dịch
Số: 0b0101 = 5
Lũy thừa của hai: 0 + 2^2 + 0 + 2^0

Sau khi dịch
Số: 0b0010 = 2
Lũy thừa của hai: 0 + 0 + 2^1 + 0
```

> Xem [divideByTwo.js](divideByTwo.js) để biết thêm chi tiết.

#### Đảo Dấu

Phương thức này biến số dương thành số âm và ngược lại.
Để làm điều này, nó sử dụng phương pháp "Bù Hai" mà làm điều đó bằng cách
đảo ngược tất cả các bit của số và thêm 1 vào nó.

```
1101 -3
1110 -2
1111 -1
0000  0
0001  1
0010  2
0011  3
```

> Xem [switchSign.js](switchSign.js) để biết thêm chi tiết.

#### Nhân Hai Số Có Dấu

Phương thức này nhân hai số nguyên có dấu bằng các toán tử bitwise.
Phương thức này dựa trên các sự thật sau:

````text
a * b có thể được viết ở các định dạng sau:
  0                     nếu a là số không hoặc b là số không hoặc cả hai a và b đều là số không
  2a * (b/2)            nếu b là số chẵn
  2a * (b - 1)/2 + a    nếu b là số lẻ và dương
  2a * (b + 1)/2 - a    nếu b là số lẻ và âm
``

`

Ưu điểm của phương pháp này là trong mỗi bước đệ quy một trong các toán hạng
giảm xuống còn một nửa giá trị ban đầu của nó. Do đó, độ phức tạp thời gian chạy là `O(log(b))` với `b` là
toán hạng giảm xuống một nửa trong mỗi bước đệ quy.

> Xem [multiply.js](multiply.js) để biết thêm chi tiết.

#### Nhân Hai Số Không Dấu

Phương thức này nhân hai số nguyên bằng các toán tử bitwise.
Phương pháp này dựa trên việc "Mọi số có thể được biểu diễn dưới dạng tổng của lũy thừa của 2".

Ý tưởng chính của việc nhân theo cách bitwise là mọi số có thể được chia ra
thành tổng của lũy thừa của hai:

Ví dụ

```text
19 = 2^4 + 2^1 + 2^0
````

Sau đó, việc nhân số `x` với `19` tương đương với:

```text
x * 19 = x * 2^4 + x * 2^1 + x * 2^0
```

Bây giờ chúng ta cần nhớ rằng `x * 2^4` tương đương với dịch `x` sang trái
bởi `4` bit (`x << 4`).

> Xem [multiplyUnsigned.js](multiplyUnsigned.js) để biết thêm chi tiết.

#### Đếm Các Bit Được Đặt

Phương thức này đếm số lượng bit được đặt trong một số bằng cách sử dụng toán tử bitwise.
Ý tưởng chính là chúng ta dịch số sang phải một bit mỗi lần và kiểm tra
kết quả của phép `&` có phải là `1` nếu bit được đặt và `0` nếu không.

```text
Số: 5 = 0b0101
Số bit được đặt = 2
```

> Xem [countSetBits.js](countSetBits.js) để biết thêm chi tiết.

#### Đếm Số Bit Cần Đảo Để Chuyển Một Số Thành Số Khác

Phương thức này xuất số bit cần thiết để chuyển đổi một số thành số khác.
Điều này sử dụng thuộc tính khi các số được `XOR` thì kết quả sẽ là số
các bit khác nhau.

```
5 = 0b0101
1 = 0b0001
Số bit cần đảo: 1
```

> Xem [bitsDiff.js](bitsDiff.js) để biết thêm chi tiết.

#### Đếm Các Bit Của Một Số

Để tính toán số bit có ý nghĩa, chúng ta cần dịch `1` sang trái một bit mỗi lần
và kiểm tra xem số dịch có lớn hơn số đầu vào không.

```
5 = 0b0101
Số bit có ý nghĩa là: 3
Khi chúng ta dịch 1 bốn lần, nó sẽ trở nên lớn hơn 5.
```

> Xem [bitLength.js](bitLength.js) để biết thêm chi tiết.

#### Là Số Lũy Thừa Của Hai

Phương thức này kiểm tra xem một số có phải là lũy thừa của hai không. Nó sử dụng thuộc tính sau
là nếu `powerNumber` là một số đã được hình thành như một lũy thừa
của hai (tức là 2, 4, 8, 16 v.v.). Sau đó nếu chúng ta thực hiện phép `&` giữa `powerNumber`
và `powerNumber - 1` nó sẽ trả về `0` (trong trường hợp số là lũy thừa của hai).

```
Số: 4 = 0b0100
Số: 3 = (4 - 1) = 0b0011
4 & 3 = 0b0100 & 0b0011 = 0b0000 <-- Bằng không, là lũy thừa của hai.

Số: 10 = 0b01010
Số: 9 = (10 - 1) = 0b01001
10 & 9 = 0b01010 & 0b01001 = 0b01000 <-- Không bằng không, không phải là lũy thừa của hai.
```

> Xem [isPowerOfTwo.js](isPowerOfTwo.js) để biết thêm chi tiết.

#### Bộ Cộng Đầy Đủ

Phương thức này cộng hai số nguyên bằng cách sử dụng toán tử bitwise.

Nó thực hiện mạch điện tử [full adder](<https://en.wikipedia.org/wiki/Adder_(electronics)>)
để cộng hai số nguyên 32 bit trong định dạng bù hai.
Nó sử dụng logic boolean để bao phủ tất cả các trường hợp có thể của việc cộng hai bit đầu vào:
có và không có một "carry bit" từ việc cộng giai đoạn trước đó ít quan trọng hơn.

Chú thích:

- `A`: Số `A`
- `B`: Số `B`
- `ai`: bit thứ i của số `A`
- `bi`: bit thứ i của số `B`
- `carryIn`: một bit được mang từ giai đoạn ít quan trọng hơn trước đó
- `carryOut`: một bit được mang đến

giai đoạn quan trọng hơn tiếp theo

- `bitSum`: Tổng của `ai`, `bi`, và `carryIn`
- `resultBin`: Kết quả đầy đủ của việc cộng giai đoạn hiện tại với tất cả các giai đoạn ít quan trọng hơn (ở dạng nhị phân)
- `resultDec`: Kết quả đầy đủ của việc cộng giai đoạn hiện tại với tất cả các giai đoạn ít quan trọng hơn (ở dạng thập phân)

```
A = 3: 011
B = 6: 110
┌──────┬────┬────┬─────────┬──────────┬─────────┬───────────┬───────────┐
│  bit │ ai │ bi │ carryIn │ carryOut │  bitSum │ resultBin │ resultDec │
├──────┼────┼────┼─────────┼──────────┼─────────┼───────────┼───────────┤
│   0  │ 1  │ 0  │    0    │    0     │     1   │       1   │     1     │
│   1  │ 1  │ 1  │    0    │    1     │     0   │      01   │     1     │
│   2  │ 0  │ 1  │    1    │    1     │     0   │     001   │     1     │
│   3  │ 0  │ 0  │    1    │    0     │     1   │    1001   │     9     │
└──────┴────┴────┴─────────┴──────────┴─────────┴───────────┴───────────┘
```

> Xem [fullAdder.js](fullAdder.js) để biết thêm chi tiết.
> Xem [Full Adder trên YouTube](https://www.youtube.com/watch?v=wvJc9CZcvBc&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8).

## Tài Liệu Tham Khảo

- [Bit Manipulation trên YouTube](https://www.youtube.com/watch?v=NLKQEOgBAnw&t=0s&index=28&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [Số Âm trong nhị phân trên YouTube](https://www.youtube.com/watch?v=4qH4unVtJkE&t=0s&index=30&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [Những Mẹo Bit trên stanford.edu](https://graphics.stanford.edu/~seander/bithacks.html)
