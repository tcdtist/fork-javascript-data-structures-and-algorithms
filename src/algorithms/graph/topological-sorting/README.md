# Sắp xếp Topo - Topological Sorting

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

Trong lĩnh vực khoa học máy tính, sắp xếp topo hoặc sắp xếp topo của một đồ thị có hướng là một thứ tự tuyến tính của các đỉnh sao cho đối với mỗi cạnh có hướng `uv` từ đỉnh `u` đến đỉnh `v`, `u` đến trước `v` trong thứ tự.

Ví dụ, các đỉnh của đồ thị có thể đại diện cho các nhiệm vụ cần thực hiện, và các cạnh có thể đại diện cho các ràng buộc rằng một nhiệm vụ phải được thực hiện trước nhiệm vụ khác; trong ứng dụng này, một thứ tự topo chỉ là một chuỗi hợp lệ cho các nhiệm vụ.

Một thứ tự topo chỉ có thể có nếu đồ thị không có chu trình có hướng, tức là nếu nó là một [đồ thị không chu trình có hướng](https://en.wikipedia.org/wiki/Directed_acyclic_graph) (DAG). Mọi DAG đều có ít nhất một thứ tự topo, và có các thuật toán để xây dựng thứ tự topo của bất kỳ DAG nào trong thời gian tuyến tính.

![Directed Acyclic Graph](https://upload.wikimedia.org/wikipedia/commons/c/c6/Topological_Ordering.svg)

Một thứ tự topo của một đồ thị không chu trình có hướng: mỗi cạnh đi từ trước trong thứ tự (trên cùng bên trái) đến sau trong thứ tự (dưới cùng bên phải). Một đồ thị có hướng là không chu trình khi và chỉ khi nó có một thứ tự topo.

## Ví dụ

![Topologic Sorting](https://upload.wikimedia.org/wikipedia/commons/0/03/Directed_acyclic_graph_2.svg)

Đồ thị được hiển thị ở trên có nhiều thứ tự topo hợp lệ, bao gồm:

- `5, 7, 3, 11, 8, 2, 9, 10` (trực quan từ trái sang phải, từ trên xuống dưới)
- `3, 5, 7, 8, 11, 2, 9, 10` (đỉnh có số nhỏ nhất có sẵn đầu tiên)
- `5, 7, 3, 8, 11, 10, 9, 2` (ít cạnh nhất đầu tiên)
- `7, 5, 11, 3, 10, 8, 9, 2` (đỉnh có số lớn nhất có sẵn đầu tiên)
- `5, 7, 11, 2, 3, 8, 9, 10` (cố gắng từ trên xuống dưới, từ trái sang phải)
- `3, 7, 8, 5, 11, 10, 2, 9` (tùy ý)

## Ứng dụng

Ứng dụng chuẩn của sắp xếp topo là trong **lập lịch một chuỗi công việc** hoặc nhiệm vụ dựa trên sự phụ thuộc của chúng. Các công việc được đại diện bởi các đỉnh, và có một cạnh từ `x` đến `y` nếu công việc `x` phải hoàn thành trước khi công việc `y` có thể bắt đầu (ví dụ, khi giặt quần áo, máy giặt phải hoàn thành trước khi chúng ta cho quần áo vào máy sấy). Sau đó, một thứ tự topo cung cấp một thứ tự để thực hiện các công việc.

Ứng dụng khác là **giải quyết phụ thuộc**. Mỗi đỉnh là một gói và mỗi cạnh là một sự phụ thuộc của gói `a` vào gói 'b'. Sau đó, sắp xếp topo sẽ cung cấp một chuỗi cài đặt các phụ thuộc một cách mà mỗi phụ thuộc tiếp theo đã có các gói phụ thuộc của nó được cài đặt trước.

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Topological_sorting)
- [Sắp xếp Topo trên YouTube bởi Tushar Roy](https://www.youtube.com/watch?v=ddTC4Zovtbc&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
