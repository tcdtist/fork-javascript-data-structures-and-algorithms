# Bài toán người bán hàng du lịch - Travelling Salesman Problem (TSP)

_Đọc tài liệu này bằng ngôn ngữ khác:_
[_Tiếng Anh_](README.en-EN.md)

Bài toán người bán hàng du lịch (TSP) đặt ra câu hỏi sau:
"Cho một danh sách các thành phố và khoảng cách giữa từng cặp thành phố, đâu là tuyến đường ngắn nhất có thể đi qua mỗi thành phố và trở về thành phố xuất phát?"

![Travelling Salesman](https://upload.wikimedia.org/wikipedia/commons/1/11/GLPK_solution_of_a_travelling_salesman_problem.svg)

Giải pháp cho bài toán người bán hàng du lịch: đường màu đen chỉ lộ trình ngắn nhất có thể nối mọi điểm đỏ.

![Travelling Salesman Graph](https://upload.wikimedia.org/wikipedia/commons/3/30/Weighted_K4.svg)

TSP có thể được mô hình hóa như một đồ thị vô hướng có trọng số, trong đó các thành phố là các đỉnh của đồ thị, các lối đi là các cạnh của đồ thị, và khoảng cách của một lối đi là trọng số của cạnh đó. Đây là một bài toán tối ưu hóa bắt đầu và kết thúc tại một đỉnh xác định sau khi đã thăm mỗi đỉnh khác đúng một lần. Thường thì mô hình là một đồ thị hoàn chỉnh (tức là mỗi cặp đỉnh đều được nối với nhau bằng một cạnh). Nếu không có lối đi tồn tại giữa hai thành phố, việc thêm một cạnh tùy ý dài sẽ hoàn thành đồ thị mà không ảnh hưởng đến chuyến đi tối ưu.

## Tài liệu tham khảo

- [Wikipedia](https://en.wikipedia.org/wiki/Travelling_salesman_problem)
