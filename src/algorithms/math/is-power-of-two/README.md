# Is a power of two - Là Lũy Thừa Của Hai

_Xem bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Cho một số nguyên dương, hãy viết một hàm để kiểm tra xem nó có phải là lũy thừa của hai hay không.

**Giải pháp Naive**

Trong giải pháp Naive, chúng ta chỉ cần tiếp tục chia số cho hai cho đến khi số trở thành `1` và mỗi lần làm như vậy, chúng ta kiểm tra rằng phần dư sau khi chia luôn là `0`. Nếu không, số đó không thể là một lũy thừa của hai.

**Giải pháp Bitwise**

Các lũy thừa của hai trong hệ nhị phân luôn chỉ có một bit được thiết lập. Duy nhất ngoại lệ là với một số nguyên có dấu (ví dụ: một số nguyên có dấu 8 bit với giá trị -128 sẽ trông như sau: `10000000`)

```
1: 0001
2: 0010
4: 0100
8: 1000
```

Vì vậy, sau khi kiểm tra số có lớn hơn không, chúng ta có thể sử dụng một phép toán bitwise để kiểm tra rằng chỉ có một bit được thiết lập.

```
số & (số - 1)
```

Ví dụ cho số `8`, phép toán đó sẽ như sau:

```
  1000
- 0001
  ----
  0111

  1000
& 0111
  ----
  0000
```

## Tài Liệu Tham Khảo

- [GeeksForGeeks](https://www.geeksforgeeks.org/program-to-find-whether-a-no-is-power-of-two/)
- [Giải pháp Bitwise trên Stanford](http://www.graphics.stanford.edu/~seander/bithacks.html#DetermineIfPowerOf2)
- [Phép trừ số nhị phân trên YouTube](https://www.youtube.com/watch?v=S9LJknZTyos&t=0s&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=66)
