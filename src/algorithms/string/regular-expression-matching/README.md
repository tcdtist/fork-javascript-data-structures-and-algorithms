# Khớp Biểu Thức Chính Quy

_Nhấn vào đây để đọc bằng ngôn ngữ khác:_
[_English_](README.en-EN.md)

Cho một chuỗi đầu vào `s` và một mẫu `p`, hãy thực hiện việc khớp biểu thức chính quy với hỗ trợ cho `.` và `*`.

- `.` Khớp với bất kỳ ký tự nào.
- `*` Khớp với không hoặc nhiều hơn một phần tử trước đó.

Việc khớp này nên bao gồm **toàn bộ** chuỗi đầu vào (không phải là một phần).

**Ghi Chú**

- `s` có thể trống và chỉ chứa các chữ cái thường `a-z`.
- `p` có thể trống và chỉ chứa các chữ cái thường `a-z`, và các ký tự như `.` hoặc `*`.

## Ví dụ

**Ví dụ #1**

Đầu vào:

```
s = 'aa'
p = 'a'
```

Đầu ra: `false`

Giải thích: `a` không khớp với toàn bộ chuỗi `aa`.

**Ví dụ #2**

Đầu vào:

```
s = 'aa'
p = 'a*'
```

Đầu ra: `true`

Giải thích: `*` có nghĩa là không hoặc nhiều hơn một phần tử trước đó, `a`.
Do đó, bằng cách lặp lại `a` một lần, nó trở thành `aa`.

**Ví dụ #3**

Đầu vào:

```
s = 'ab'
p = '.*'
```

Đầu ra: `true`

Giải thích: `.*` có nghĩa là "không hoặc nhiều hơn (`*`) bất kỳ ký tự nào (`.`)".

**Ví dụ #4**

Đầu vào:

```
s = 'aab'
p = 'c*a*b'
```

Đầu ra: `true`

Giải thích: `c` có thể được lặp lại 0 lần, `a` có thể được lặp lại
1 lần. Do đó nó khớp với `aab`.

## Tham Khảo

- [YouTube](https://www.youtube.com/watch?v=l3hda49XcDE&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8&index=71&t=0s)
- [LeetCode](https://leetcode.com/problems/regular-expression-matching/description/)
