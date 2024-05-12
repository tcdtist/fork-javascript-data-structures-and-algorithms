# Vấn đề N Hậu

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

**Bài toán bát quân hậu** là bài toán về việc đặt tám quân hậu trên một bàn cờ vua `8×8` sao cho không có hai quân hậu nào đe dọa nhau. Do đó, một giải pháp yêu cầu không có hai quân hậu nào chia sẻ cùng một hàng, cột hoặc đường chéo. Bài toán bát quân hậu là một ví dụ của **bài toán n quân hậu** tổng quát hơn, trong đó đặt n quân hậu không đe dọa lẫn nhau trên một bàn cờ vua `n×n`, và giải pháp tồn tại cho tất cả các số tự nhiên `n` ngoại trừ `n=2` và `n=3`.

Ví dụ, dưới đây là một giải pháp cho bài toán 4 Quân hậu.

![N Queens](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/N_Queen_Problem.jpg)

Kết quả mong đợi là một ma trận nhị phân có giá trị 1 cho các ô mà quân hậu được đặt. Ví dụ sau đây là ma trận kết quả cho giải pháp 4 quân hậu ở trên.

```
{ 0,  1,  0,  0}
{ 0,  0,  0,  1}
{ 1,  0,  0,  0}
{ 0,  0,  1,  0}
```

## Thuật toán Ngu Naïve

Tạo tất cả các cấu hình có thể của quân hậu trên bàn cờ và in ra một cấu hình thỏa mãn các ràng buộc đã cho.

```
khi còn các cấu hình chưa thử
{
   tạo cấu hình tiếp theo
   nếu các quân hậu không đe dọa trong cấu hình này thì
   {
      in ra cấu hình này;
   }
}
```

## Thuật toán Backtracking

Ý tưởng là đặt các quân hậu một cách tuần tự trong các cột khác nhau, bắt đầu từ cột trái nhất. Khi chúng ta đặt một quân hậu trong một cột, chúng ta kiểm tra xem có xung đột với các quân hậu đã đặt trước đó không. Trong cột hiện tại, nếu chúng ta tìm thấy một hàng mà không có xung đột, chúng ta đánh dấu hàng và cột này là một phần của giải pháp. Nếu chúng ta không tìm thấy hàng đó do xung đột, chúng ta quay lại và trả về giá trị sai.

```
1) Bắt đầu từ cột trái nhất
2) Nếu tất cả quân hậu đã được đặt trả về true
3) Thử tất cả các hàng trong cột hiện tại. Làm theo mỗi hàng đã thử.
    a) Nếu quân hậu có thể được đặt an toàn trong hàng này thì đánh dấu [hàng, cột] này là một phần của giải pháp và kiểm tra đệ quy xem việc đặt quân hậu ở đây dẫn đến một giải pháp hay không.
    b) Nếu việc đặt quân hậu ở [hàng, cột] dẫn đến một giải pháp thì trả về true.
    c) Nếu việc đặt quân hậu không dẫn đến một giải pháp thì hủy đánh dấu [hàng, cột] này (Backtrack) và đi đến bước (a) để thử các hàng khác.
3) Nếu tất cả các hàng đã được thử và không có gì hoạt động, trả về false để kích
    hoạt quay lại.
```

## Giải Pháp Bitwise

Thuật toán bitwise cơ bản tiếp cận vấn đề như sau:

- Quân hậu có thể đe dọa theo đường chéo, dọc hoặc ngang. Do đó, chỉ có thể có một quân hậu trong mỗi hàng, một trong mỗi cột và tối đa một trong mỗi đường chéo.
- Vì chúng ta biết chỉ có một quân hậu trên mỗi hàng, chúng ta sẽ bắt đầu ở hàng đầu tiên, đặt một quân hậu, sau đó di chuyển đến hàng thứ hai, đặt quân hậu thứ hai và tiếp tục cho đến khi a) chúng ta đạt được một giải pháp hợp lệ hoặc b) chúng ta đạt đến một thứ tự "tử thua" (tức là chúng ta không thể đặt một quân hậu sao cho nó "an toàn" từ các quân hậu khác).
- Vì chúng ta chỉ đặt một quân hậu trên mỗi hàng, nên chúng ta không cần phải lo lắng về các cuộc tấn công ngang, vì không có quân hậu nào sẽ bao giờ ở trên cùng một hàng với quân hậu khác.
- Điều đó có nghĩa là chúng ta chỉ cần kiểm tra ba điều trước khi đặt một quân hậu vào một ô nhất định: 1) Cột của ô đó không có bất kỳ quân hậu nào khác, 2) đường chéo trái của ô đó không có quân hậu nào khác, và 3) đường chéo phải của ô đó không có quân hậu nào khác.
- Nếu chúng ta bao giờ đạt đến một điểm nơi không có nơi an toàn nào để đặt một quân hậu, chúng ta có thể từ bỏ nỗ lực hiện tại của mình và ngay lập tức thử nghiệm các khả năng tiếp theo.

Trước hết hãy nói về hàm đệ quy. Bạn sẽ nhận thấy rằng nó chấp nhận 3 tham số: `leftDiagonal`, `column`, và `rightDiagonal`. Mỗi tham số này kỹ thuật là một số nguyên, nhưng thuật toán tận dụng việc rằng một số nguyên được biểu diễn bằng một chuỗi bit. Vì vậy, hãy nghĩ về mỗi tham số này như một chuỗi gồm `N` bit.

Mỗi bit trong mỗi tham số này đại diện cho việc ô tương ứng trên hàng hiện tại "có sẵn" hay không.

Ví dụ:

- Với `N=4`, cột có giá trị `0010` sẽ có nghĩa là cột thứ 3 đã bị chiếm bởi một quân hậu.
- Với `N=8`, ld có giá trị `00011000` tại hàng 5 sẽ có nghĩa là các đường chéo từ trên xuống dưới qua cột 4 và 5 của hàng đó đã bị chiếm bởi quân hậu.

Dưới đây là một hình minh họa cho `leftDiagonal`, `column`, và `rightDiagonal`.

![](http://gregtrowbridge.com/content/images/2014/Jul/Screenshot-from-2014-06-17-19-46-20.png)

## Tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Eight_queens_puzzle)
- [GeeksForGeeks](https://www.geeksforgeeks.org/backtracking-set-3-n-queen-problem/)
- [Trên YouTube bởi Abdul Bari](https://www.youtube.com/watch?v=xFv_Hl4B83A&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [Trên YouTube bởi Tushar Roy](https://www.youtube.com/watch?v=xouin83ebxE&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- Giải Pháp Bitwise
  - [Wikipedia](https://en.wikipedia.org/wiki/Eight_queens_puzzle)
  - [Giải pháp của Greg Trowbridge](http://gregtrowbridge.com/a-bitwise-solution-to-the-n-queens-problem-in-javascript/)
