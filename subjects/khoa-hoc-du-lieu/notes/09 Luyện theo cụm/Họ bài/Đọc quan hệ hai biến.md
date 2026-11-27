# Đọc quan hệ hai biến

**Cần biết trước.** [Chương 07 - Chọn và đọc biểu đồ](../../07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md).

**Quy trình giải.** Đọc lần lượt ánh xạ x–y, kiểu đánh dấu và mã hóa bổ sung. Với nhiều điểm, xem mật độ chồng lấn trước khi kết luận.

Làm từng bài trước khi mở gợi ý, rồi so sánh quy tắc với bài trước.

## 1 · Cơ bản

Đoạn mã sau vẽ cái gì?

```python
import matplotlib.pyplot as plt
plt.plot([1, 2, 3], [1, 4, 9])
plt.scatter([1, 2, 3], [1, 4, 9], color='red')
plt.show()
```

- **A.** Chỉ có ba điểm phân tán màu đỏ vì scatter được vẽ sau và xoá đường của plot
- **B.** Chỉ có một đường nối màu xanh dương vì scatter không vẽ chồng lên cùng Axes
- **C.** Đường nối màu xanh dương và ba điểm phân tán màu đỏ nằm đúng trên các tọa độ đó
- **D.** Một biểu đồ cột gồm ba cột có chiều cao 1, 4 và 9 với đường viền màu đỏ

ID ScoreUp: `Q03040`

> **hint** Gợi ý 1
> Xác định khái niệm hoặc quy tắc được hỏi.

> **hint** Gợi ý 2
> Đọc lần lượt ánh xạ x–y, kiểu đánh dấu và mã hóa bổ sung. Với nhiều điểm, xem mật độ chồng lấn trước khi kết luận.

> **check** Bài mẫu giải đầy đủ
> **C.** plot nối các cặp tọa độ thành đường, scatter đánh dấu đúng các tọa độ đó bằng các điểm đỏ.

## 2 · Vận dụng

Scatter plot giữa tuổi của nhân viên (trục x) và năng suất làm việc (trục y) cho thấy các điểm xếp theo hình chữ U ngược: năng suất tăng đến khoảng 40 tuổi rồi giảm dần. Kết luận nào phù hợp nhất?

- **A.** Quan hệ phi tuyến, nên một đường thẳng sẽ mô tả dữ liệu kém
- **B.** Tuổi và năng suất độc lập hoàn toàn nên không có mối quan hệ nào
- **C.** Cần chuyển sang biểu đồ tròn để thấy quan hệ này rõ hơn
- **D.** Quan hệ tuyến tính dương mạnh giữa tuổi và năng suất

ID ScoreUp: `Q03122`

> **hint** Gợi ý 1
> Gạch dữ kiện có ảnh hưởng đến kết quả.

> **hint** Gợi ý 2
> Đọc lần lượt ánh xạ x–y, kiểu đánh dấu và mã hóa bổ sung. Với nhiều điểm, xem mật độ chồng lấn trước khi kết luận.

> **check** Lời giải
> **A.** Quan hệ quan sát được có dạng phi tuyến. Tương quan tuyến tính đơn lẻ dễ bỏ qua quy luật cong.

## 3 · Vận dụng mở rộng

Biểu đồ phân tán của 20.000 giao dịch (giá trị đơn hàng và số lượng) có các điểm đè lên nhau thành mảng đặc, khó biết vùng nào đông nhất. Tham số nào của ax.scatter giúp giải quyết tốt nhất?

- **A.** c='black' để mọi điểm cùng một màu đen đậm, giúp thấy rõ vùng dày đặc nhất
- **B.** s với giá trị rất lớn như 500 để mỗi điểm lớn hơn và nổi bật hơn trên đồ thị
- **C.** alpha nhỏ như 0.1 để điểm trong suốt, vùng chồng nhiều điểm sẽ hiện đậm hơn
- **D.** label='giao dich' để gắn nhãn nhóm điểm và hiển thị mật độ trong chú giải

ID ScoreUp: `Q03223`

> **hint** Gợi ý 1
> Viết trạng thái trung gian hoặc xác định tác động của từng thao tác.

> **hint** Gợi ý 2
> Đọc lần lượt ánh xạ x–y, kiểu đánh dấu và mã hóa bổ sung. Với nhiều điểm, xem mật độ chồng lấn trước khi kết luận.

> **check** Lời giải
> **C.** Giảm alpha để từng điểm bán trong suốt và vùng có nhiều điểm trông đậm hơn.
