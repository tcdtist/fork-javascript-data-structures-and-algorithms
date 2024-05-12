# Bài toán Cầu Thang Đệ Quy

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

## Vấn đề

Có `n` bậc cầu thang, một người đứng ở dưới muốn đến đỉnh. Người đó có thể leo `1` hoặc `2` bậc cầu thang mỗi lần. _Đếm số cách mà người đó có thể đến được đỉnh._

![](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/nth-stair.png)

## Giải Pháp

Đây là một vấn đề thú vị vì có nhiều cách để giải quyết mà minh họa các phương pháp lập trình khác nhau.

- [Giải Pháp Đệ Quy Brute Force](./recursiveStaircaseBF.js) - Thời gian: `O(2^n)`; Không gian: `O(1)`
- [Giải Pháp Đệ Quy Với Ghi Nhớ](./recursiveStaircaseMEM.js) - Thời gian: `O(n)`; Không gian: `O(n)`
- [Giải Pháp Lập Trình Động](./recursiveStaircaseDP.js) - Thời gian: `O(n)`; Không gian: `O(n)`
- [Giải Pháp Lặp](./recursiveStaircaseIT.js) - Thời gian: `O(n)`; Không gian: `O(1)`

## Tham Khảo

- [Trên YouTube bởi Gayle Laakmann McDowell](https://www.youtube.com/watch?v=eREiwuvzaUM&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=81&t=0s)
- [GeeksForGeeks](https://www.geeksforgeeks.org/count-ways-reach-nth-stair/)
