# Sai số hồi quy

**Cần biết trước.** [Chương 08 - Hồi quy và KNN](../../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md).

**Quy trình giải.** Viết vector phần dư trước, lấy trị tuyệt đối cho MAE, bình phương rồi lấy trung bình cho MSE, và lấy căn cuối cùng cho RMSE.

Làm từng bài trước khi mở gợi ý, rồi so sánh quy tắc với bài trước.

## 1 · Cơ bản

RMSE là gì và nó có liên quan gì với MSE?

- **A.** RMSE = MSE / 2, chỉ khác MSE về độ lớn chứ không khác về đơn vị
- **B.** RMSE = MSE², có đơn vị là bình phương đơn vị của giá trị thực y
- **C.** RMSE = sqrt(MSE), có cùng đơn vị với giá trị thực y
- **D.** RMSE = MSE / mean(y), là một tỷ lệ phần trăm không có đơn vị

ID ScoreUp: `Q03481`

> **hint** Gợi ý 1
> Xác định khái niệm hoặc quy tắc được hỏi.

> **hint** Gợi ý 2
> Viết vector phần dư trước, lấy trị tuyệt đối cho MAE, bình phương rồi lấy trung bình cho MSE, và lấy căn cuối cùng cho RMSE.

> **check** Bài mẫu giải đầy đủ
> **C.** RMSE là căn của MSE và cùng đơn vị với mục tiêu.

## 2 · Vận dụng

Trong việc đánh giá mô hình cho bài toán hồi quy. Giá trị thực tế là [10, 20], giá trị dự đoán là [12, 19]. Tính MSE?

- **A.** 1.5
- **B.** 2.5
- **C.** 5
- **D.** 0

ID ScoreUp: `Q03456`

> **hint** Gợi ý 1
> Gạch dữ kiện có ảnh hưởng đến kết quả.

> **hint** Gợi ý 2
> Viết vector phần dư trước, lấy trị tuyệt đối cho MAE, bình phương rồi lấy trung bình cho MSE, và lấy căn cuối cùng cho RMSE.

> **check** Lời giải
> **B.** Phần dư có độ lớn 2 và 1. Bình phương rồi lấy trung bình cho MSE bằng 2,5.

## 3 · Vận dụng mở rộng

Chương trình in MAE và RMSE của hai mô hình dự đoán đơn giá. Kết luận nào phù hợp với kết quả in ra?


```python
import numpy as np
from sklearn.metrics import mean_absolute_error, mean_squared_error

y_true = np.array([100, 100, 100, 100])
pred_a = np.array([100, 100, 100, 60])
pred_b = np.array([90, 110, 90, 110])

print("A:", mean_absolute_error(y_true, pred_a), np.sqrt(mean_squared_error(y_true, pred_a)))
print("B:", mean_absolute_error(y_true, pred_b), np.sqrt(mean_squared_error(y_true, pred_b)))
```
- **A.** MAE bằng nhau nhưng RMSE của A gấp đôi vì A có một lần dự đoán lệch rất lớn
- **B.** Mô hình B tốt hơn ở cả hai chỉ số vì RMSE của B nhỏ hơn và MAE của B cũng nhỏ hơn
- **C.** Hai mô hình có chất lượng như nhau vì MAE bằng nhau, RMSE khác nhau do sai số làm tròn
- **D.** Mô hình A có sai số trung bình gấp đôi mô hình B vì RMSE của A bằng 20 còn B bằng 10

ID ScoreUp: `Q03478`

> **hint** Gợi ý 1
> Viết trạng thái trung gian hoặc xác định tác động của từng thao tác.

> **hint** Gợi ý 2
> Viết vector phần dư trước, lấy trị tuyệt đối cho MAE, bình phương rồi lấy trung bình cho MSE, và lấy căn cuối cùng cho RMSE.

> **check** Lời giải
> **A.** A và B đều có MAE 10. RMSE của A là 20, của B là 10, vì A dồn toàn bộ lỗi vào một mẫu.
