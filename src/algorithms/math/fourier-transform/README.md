# Phép Biến Đổi Fourier

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

## Định nghĩa

**Phép biến đổi Fourier** (**FT**) phân tách một hàm của thời gian (một tín hiệu) thành các tần số tạo thành nó, tương tự như cách một hợp âm nhạc có thể được biểu diễn dưới dạng các tần số (hoặc nốt âm) của các nốt nhạc thành phần của nó.

**Biến đổi Fourier Rời rạc** (**DFT**) chuyển đổi một chuỗi hữu hạn các mẫu cách đều của một hàm thành một chuỗi cùng chiều dài các mẫu cách đều của phép biến đổi Fourier trong thời gian rời rạc (DTFT), mà là một hàm phức giá trị của tần số. Khoảng cách mà DTFT được lấy mẫu là nghịch đảo của thời gian của chuỗi đầu vào. Một DFT nghịch đảo là một chuỗi Fourier, sử dụng các mẫu DTFT như các hệ số của các hàm sin phức ở các tần số tương ứng với DTFT. Nó có các giá trị mẫu giống như chuỗi đầu vào ban đầu. Do đó, DFT được coi là biểu diễn miền tần số của chuỗi đầu vào ban đầu. Nếu chuỗi ban đầu bao gồm tất cả các giá trị khác không của một hàm, thì DTFT của nó là liên tục (và tuần hoàn), và DFT cung cấp các mẫu cách đều của một chu kỳ. Nếu chuỗi ban đầu là một chu kỳ của một hàm tuần hoàn, thì DFT cung cấp tất cả các giá trị khác không của một chu kỳ DTFT.

Phép biến đổi Fourier rời rạc chuyển đổi một chuỗi `N` số phức:

{x<sub>n</sub>} = x<sub>0</sub>, x<sub>1</sub>, x<sub>2</sub> ..., x<sub>N-1</sub>

thành một chuỗi khác của các số phức:

{X<sub>k</sub>} = X<sub>0</sub>, X<sub>1</sub>, X<sub>2</sub> ..., X<sub>N-1</sub>

được xác định bởi:

![DFT](https://wikimedia.org/api/rest_v1/media/math/render/svg/1af0a78dc50bbf118ab6bd4c4dcc3c4ff8502223)

**Biến đổi Fourier Rời rạc Thời gian** (**DTFT**) là một dạng của phân tích Fourier mà áp dụng cho các mẫu cách đều của một hàm liên tục. Thuật ngữ thời gian rời rạc chỉ đến việc phép biến đổi hoạt động trên dữ liệu rời rạc (mẫu) mà khoảng cách của nó thường có đơn vị thời gian. Từ chỉ các mẫu, nó tạo ra một hàm của tần số là sự tổng của chu kỳ tuần hoàn của biến đổi Fourier của hàm liên tục ban đầu.

**Phép Biến Đổi Fourier Nhanh** (**FFT**) là một thuật toán mẫu một tín hiệu trong một khoảng thời gian (hoặc không gian) và phân chia nó thành các thành phần tần số của nó. Các thành phần này là các dao động sin đơn tần số riêng biệt mỗi cái có biên độ và pha riêng.

Phép biến đổi này được minh họa trong biểu đồ dưới đây. Trong khoảng thời gian được đo trong biểu đồ, tín hiệu chứa 3 tần số quan trọng riêng biệt.

Xem tín hiệu trong miền thời gian và tần số:

![FFT](https://upload.wikimedia.org/wikipedia/commons/6/61/FFT-Time-Frequency-View.png)

Một thuật toán FFT tính phép biến đổi Fourier rời rạc (DFT) của một chuỗi, hoặc phép nghịch đảo của nó (IFFT). Phân tích Fourier chuyển đổi một tín hiệu từ miền ban đầu của nó thành một biểu diễn trong miền tần số và ngược lại. Một FFT tính toán nhanh chóng các biến đổi như vậy bằng cách phân tách ma trận DFT thành một tích của các yếu tố thưa (phần lớn là không) số lượng. Do đó, nó quản lý giảm độ phức tạp của việc tính toán DFT từ O(n<sup>2</sup>), mà phát sinh nếu một cách đơn giản áp dụng định nghĩa của DFT, xuống O(n log n), trong đó n là kích thước dữ liệu.

Dưới đây là một phân tích Fourier rời rạc của một tổng của sóng cosin tại 10, 20, 30, 40 và 50 Hz:

![FFT](https://upload.wikimedia.org/wikipedia/commons/6/64/FFT_of_Cosine_Summation_Function.png)

## Giải thích

Phép Biến Đổi Fourier là một trong những hiểu biết sâu sắc nhất từng được thực hiện. Thật không may, ý nghĩa bị chôn vùi trong các phương trình dày đặc:

![](https://betterexplained.com/wp-content/plugins/wp-latexrender/pictures/45c088dbb767150fc0bacfeb49dd49e5.png)

và

![](https://betterexplained.com/wp-content/plugins/wp-latexrender/pictures/faeb9c5bf2e60add63ae4a70b293c7b4.png)

Thay vì nhảy vào các biểu tượng, hãy trải nghiệm ý tưởng chính trực tiếp. Dưới đây là một phép phép dụng ngôn ngữ bằng tiếng Anh:

- _Phép Biến Đổi Fourier làm gì?_ Cho một smoothie, nó tìm ra công thức.
- _Làm thế nào?_ Chạy smoothie qua bộ lọc để trích xuất mỗi thành phần.
- _Tại sao?_ Công thức dễ phân tích, so sánh và sửa đổi hơn smoothie.
- _Làm sao để có smoothie trở lại?_ Trộn các thành phần.

**Hãy Suy Nghĩ Với Hình Tròn, Không Chỉ Các Hàm Sin**

Phép Biến Đổi Fourier liên quan đến các đường tròn (không chỉ là các hàm sin 1 chiều) và công thức Euler là một cách thông minh để tạo ra chúng:

![](https://betterexplained.com/wp-content/uploads/euler/equal_paths.png)

Chúng ta phải sử dụng số mũ ảo để di chuyển trong một vòng tròn không? Không cần. Nhưng nó tiện lợi và gọn gàng. Và đương nhiên, chúng ta có thể mô tả quỹ đạo của mình như là sự di chuyển đồng tọa độ trong hai chiều (thực và ảo), nhưng đừng quên cái nhìn tổng thể: chúng ta chỉ đang di chuyển trong một vòng tròn.

**Khám Phá Toàn Bộ Biến Đổi**

Ý tưởng lớn: tín hiệu của chúng ta chỉ là một loạt các tín hiệu spike thời gian! Nếu chúng ta kết hợp các công thức cho mỗi tín hiệu spike thời gian, chúng ta sẽ có công thức cho tín hiệu đầy đủ.

Phép Biến Đổi Fourier xây dựng công thức theo tần số:

![](https://betterexplained.com/wp-content/uploads/images/fourier-explained-20121219-224649.png)

Một vài ghi chú:

- N = số lượng mẫu thời gian chúng ta có
- n = mẫu hiện tại chúng ta đang xem xét (0 ... N-1)
- x<sub>n</sub> = giá trị của tín hiệu tại thời gian n
- k = tần số hiện tại chúng ta đang xem xét (0 Hertz lên tới N-1 Hertz)
- X<sub>k</sub> = lượng tần số k trong tín hiệu (biên độ và pha, một số phức)
- Yếu tố 1/N thường được di chuyển sang biến đổi nghịch đảo (đi từ tần số trở lại thời gian). Điều này được cho phép, mặc dù tôi thích 1/N trong biến đổi xuất phát vì nó cung cấp các kích thước thực sự cho các tín hiệu spike thời gian. Bạn có thể trở nên hoang đường và thậm chí sử dụng 1/sqrt(N) trên cả hai biến đổi (đi từ trước và đi lại tạo ra yếu tố 1/N).

- n/N là phần trăm thời gian chúng ta đã đi qua. 2 _ pi _ k là tốc độ của chúng ta theo radian / giây. e^-ix là quỹ đạo tròn di chuyển ngược của chúng ta. Sự kết hợp là chúng ta đã di chuyển bao xa, cho tốc độ và thời gian này.
- Các phương trình gốc cho Biến Đổi Fourier chỉ đơn giản nói "thêm các số phức". Nhiều ngôn ngữ lập trình không thể xử lý trực tiếp các số phức, vì vậy bạn chuyển tất cả mọi thứ sang tọa độ hình chữ nhật và thêm chúng.

Stuart Riffle có một cách giải thích tuyệt vời về Phép Biến Đổi Fourier:

![](https://betterexplained.com/wp-content/uploads/images/DerivedDFT.png)

## Tài Liệu Tham Khảo

- [Hướng dẫn tương tác về Biến Đổi Fourier](https://betterexplained.com/articles/an-interactive-guide-to-the-fourier-transform/)
- [DFT trên YouTube bởi Better Explained](https://www.youtube.com/watch?v=iN0VG9N2q0U&t=0s&index=77&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [FT trên YouTube bởi 3Blue1Brown](https://www.youtube.com/watch?v=spUNpyF58BY&t=0s&index=76&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [FFT trên YouTube bởi Simon Xu](https://www.youtube.com/watch?v=htCj9exbGo0&index=78&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&t=0s)
- Wikipedia
  - [FT](https://en.wikipedia.org/wiki/Fourier_transform)
  - [DFT](https://www.wikiwand.com/en/Discrete_Fourier_transform)
  - [DTFT](https://en.wikipedia.org/wiki/Discrete-time_Fourier_transform)
  - [FFT](https://www.wikiwand.com/en/Fast_Fourier_transform)
