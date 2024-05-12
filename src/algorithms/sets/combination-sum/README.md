# Combination Sum Problem - Vấn đề Tổ hợp Tổng

_Đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Cho một **tập hợp** các số ứng viên (`candidates`) **(không có phần tử trùng lặp)** và một số mục tiêu (`target`), hãy tìm tất cả các tổ hợp duy nhất trong `candidates` sao cho tổng các số ứng viên bằng `target`.

**Cùng** một số lặp lại có thể được chọn từ `candidates` không giới hạn lần.

**Ghi chú:**

- Tất cả các số (bao gồm cả `target`) sẽ là các số nguyên dương.
- Tập hợp giải pháp không được chứa các tổ hợp trùng lặp.

## Ví dụ

```
Input: candidates = [2,3,6,7], target = 7,

Một tập hợp giải pháp là:
[
  [7],
  [2,2,3]
]
```

```
Input: candidates = [2,3,5], target = 8,

Một tập hợp giải pháp là:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
```

## Giải thích

Vì vấn đề là lấy tất cả các kết quả có thể, không phải là tốt nhất hoặc số lượng kết quả, do đó chúng ta không cần xem xét DP (programing dynamic), cần sử dụng phương pháp backtracking sử dụng đệ quy để xử lý nó.

Dưới đây là một ví dụ về cây quyết định cho tình huống khi `candidates = [2, 3]` và `target = 6`:

```
                0
              /   \
           +2      +3
          /   \      \
       +2       +3    +3
      /  \     /  \     \
    +2    ✘   ✘   ✘     ✓
   /  \
  ✓    ✘
```

## Tài liệu tham khảo

- [LeetCode](https://leetcode.com/problems/combination-sum/description/)
