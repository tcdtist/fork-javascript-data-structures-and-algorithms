# Bài toán dãy con liên tục có tổng lớn nhất

_Đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Bài toán dãy con liên tục có tổng lớn nhất là nhiệm vụ của việc tìm dãy con liên tục trong một mảng một chiều, `a[1...n]`, các số trong đó có tổng lớn nhất, trong đó,

![Maximum subarray](https://wikimedia.org/api/rest_v1/media/math/render/svg/e8960f093107b71b21827e726e2bad8b023779b2)

![Maximum subarray](https://www.geeksforgeeks.org/wp-content/uploads/kadane-Algorithm.png)

## Ví dụ

Danh sách thường chứa cả số dương và số âm cùng với số `0`. Ví dụ, với mảng giá trị `−2, 1, −3, 4, −1, 2, 1, −5, 4` dãy con liên tục có tổng lớn nhất là `4, −1, 2, 1`, với tổng là `6`.

## Các giải pháp

- Giải pháp Brute Force `O(n^2)`: [bfMaximumSubarray.js](./bfMaximumSubarray.js)
- Giải pháp Chia để trị `O(n^2)`: [dcMaximumSubarraySum.js](./dcMaximumSubarraySum.js)
- Giải pháp Lập trình động `O(n)`: [dpMaximumSubarray.js](./dpMaximumSubarray.js)

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Maximum_subarray_problem)
- [YouTube](https://www.youtube.com/watch?v=ohHWQf1HDfU&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [GeeksForGeeks](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/)
- [LeetCode](https://leetcode.com/explore/interview/card/top-interview-questions-easy/97/dynamic-programming/566/discuss/1595195/C++Python-7-Simple-Solutions-w-Explanation-or-Brute-Force-+-DP-+-Kadane-+-Divide-and-Conquer)
