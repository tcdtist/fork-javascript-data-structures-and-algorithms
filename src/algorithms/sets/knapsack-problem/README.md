# Knapsack Problem - Vấn đề Knapsack (Ba lô)

_Bạn đọc bản dịch này bằng các ngôn ngữ khác:_
[_English_](README.en-EN.md)

Vấn đề ba lô, hay còn gọi là vấn đề túi rủ, là một vấn đề trong tối ưu hóa tổ hợp: Cho một tập hợp các mặt hàng, mỗi mặt hàng có trọng lượng và giá trị, hãy xác định số lượng của mỗi mặt hàng để bao gồm trong một bộ sưu tập sao cho tổng trọng lượng nhỏ hơn hoặc bằng một ngưỡng cho trước và tổng giá trị là lớn nhất có thể.

Tên của vấn đề được lấy từ tình huống mà ai đó bị ràng buộc bởi một chiếc ba lô có kích thước cố định và phải điền đầy nó với những mặt hàng có giá trị nhất.

Ví dụ về vấn đề túi rủ một chiều (hạn chế): cần chọn những hộp nào để tối đa hóa số tiền trong khi vẫn giữ trọng lượng tổng thể dưới hoặc bằng 15 kg?

![vấn đề ba lô](https://upload.wikimedia.org/wikipedia/commons/f/fd/Knapsack.svg)

## Định nghĩa

### Vấn đề túi rủ 0/1

Vấn đề phổ biến nhất được giải quyết là **vấn đề túi rủ 0/1**, giới hạn số lượng `xi` của mỗi loại mặt hàng là không hoặc một.

Cho một tập hợp các mặt hàng có số thứ tự từ `1` đến `n`, mỗi mặt hàng có trọng lượng `wi` và giá trị `vi`, cùng với một trọng lượng tối đa `W`,

tối đa ![vấn đề túi rủ 0/1](https://wikimedia.org/api/rest_v1/media/math/render/svg/85620037d368d2136fb3361702df6a489416931b)

điều kiện ![vấn đề túi rủ 0/1](https://wikimedia.org/api/rest_v1/media/math/render/svg/dd6e7c9bca4397980976ea6d19237500ce3b8176)
và ![vấn đề túi rủ 0/1](https://wikimedia.org/api/rest_v1/media/math/render/svg/07dda71da2a630762c7b21b51ea54f86f422f951)

Ở đây, `xi` đại diện cho số lượng của mỗi mặt hàng để bao gồm trong ba lô. Một cách không chính thức, vấn đề là tối đa hóa tổng giá trị của các mặt hàng trong ba lô sao cho tổng trọng lượng nhỏ hơn hoặc bằng khả năng chứa của ba lô.

### Vấn đề túi rủ có giới hạn (BKP)

**Vấn đề túi rủ có giới hạn (BKP)** loại bỏ ràng buộc là chỉ có một của mỗi mặt hàng, nhưng hạn chế số lượng `xi` bản sao của mỗi loại mặt hàng thành một giá trị số nguyên không âm tối đa `c`:

tối đa ![vấn đề túi rủ có giới hạn](https://wikimedia.org/api/rest_v1/media/math/render/svg/85620037d368d2136fb3361702df6a489416931b)

điều kiện ![vấn đề túi rủ có giới hạn](https://wikimedia.org/api/rest_v1/media/math/render/svg/dd6e7c9bca4397980976ea6d19237500ce3b8176)
và ![vấn đề túi rủ có giới hạn](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c8c5ac4f8247b3b8e01e89de76a1df0ea969821)

### Vấn đề túi rủ không giới hạn (UKP)

**Vấn đề túi rủ không giới hạn (UKP)** không đặt ra hạn chế trên số lượng bản sao của mỗi loại mặt hàng và có thể được sắp xếp như trên ngoại trừ việc rằng ràng buộc duy nhất đối với `xi` là nó phải là số nguyên không âm.

tối đa ![vấn đề túi rủ không giới hạn](https://wikimedia.org/api/rest_v1/media/math/render/svg/85620037d368d2136fb3361702df6a489416931b)

điều kiện ![vấn đề túi rủ không giới hạn](https://wikimedia.org/api/rest_v1/media/math/render/svg/dd6e7c9bca4397980976ea6d19237500ce3b8176)
và ![vấn đề túi rủ không giới hạn](https://wikimedia.org/api/rest_v1/media/math/render/svg/90a99710f61d5dea19e49ae5b31164d2b56b07e3)

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Knapsack_problem)
- [Vấn đề túi rủ 0/1 trên YouTube](https://www.youtube.com/watch?v=8LusJS5-AGo&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
