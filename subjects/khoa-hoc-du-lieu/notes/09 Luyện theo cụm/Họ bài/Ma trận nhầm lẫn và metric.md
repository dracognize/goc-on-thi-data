# Ma trận nhầm lẫn và metric

**Cần biết trước.** [Chương 08 - Ma trận nhầm lẫn và chỉ số](../../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md).

**Quy trình giải.** Đánh dấu nhãn quan tâm, sau đó chốt hàng là thật và cột là dự đoán. Precision chia theo cột của nhãn dương. Recall chia theo hàng.

Làm từng bài trước khi mở gợi ý, rồi so sánh quy tắc với bài trước.

## 1 · Cơ bản

Ma trận nhầm lẫn do Scikit-learn trả về cho nhãn 0 (âm) và 1 (dương) là `[[50, 10], [5, 35]]`, với hàng là nhãn thực tế và cột là nhãn dự đoán. Precision của lớp 1 là bao nhiêu?

- **A.** 0.88
- **B.** 0.85
- **C.** 0.78
- **D.** 0.70

ID ScoreUp: `Q03477`

> **hint** Gợi ý 1
> Xác định khái niệm hoặc quy tắc được hỏi.

> **hint** Gợi ý 2
> Đánh dấu nhãn quan tâm, sau đó chốt hàng là thật và cột là dự đoán. Precision chia theo cột của nhãn dương. Recall chia theo hàng.

> **check** Bài mẫu giải đầy đủ
> **C.** TP = 35 và FP = 10, nên precision = 35/45 ≈ 0,7778.

## 2 · Vận dụng

Tập test có 42 ca ác tính. Cây quyết định đạt Recall 0.9048 đối với lớp ác tính. Có bao nhiêu ca ác tính bị dự đoán nhầm thành lành tính?

- **A.** 3 ca
- **B.** 5 ca
- **C.** 4 ca
- **D.** 9 ca

ID ScoreUp: `Q03492`

> **hint** Gợi ý 1
> Gạch dữ kiện có ảnh hưởng đến kết quả.

> **hint** Gợi ý 2
> Đánh dấu nhãn quan tâm, sau đó chốt hàng là thật và cột là dự đoán. Precision chia theo cột của nhãn dương. Recall chia theo hàng.

> **check** Lời giải
> **C.** Khoảng 38 ca được phát hiện trong 42 ca thật, nên có 4 ca bỏ sót.

## 3 · Vận dụng mở rộng

Một nhóm phân tích dự đoán khách hàng rời bỏ dịch vụ (nhãn 0 là rời bỏ, nhãn 1 là ở lại) cho 8 khách hàng và coi rời bỏ là lớp cần quan tâm. Khi chạy mã, kết quả in ra (precision rồi recall của lớp rời bỏ) là gì?


```python
from sklearn.metrics import precision_score, recall_score

y_true = [0, 0, 0, 0, 0, 0, 1, 1]
y_pred = [0, 0, 0, 1, 1, 1, 0, 1]
print(precision_score(y_true, y_pred, pos_label=0),
      recall_score(y_true, y_pred, pos_label=0))
```
- **A.** 0.75 0.5
- **B.** 0.25 0.5
- **C.** 0.5 0.75
- **D.** 0.75 0.75

ID ScoreUp: `Q03525`

> **hint** Gợi ý 1
> Viết trạng thái trung gian hoặc xác định tác động của từng thao tác.

> **hint** Gợi ý 2
> Đánh dấu nhãn quan tâm, sau đó chốt hàng là thật và cột là dự đoán. Precision chia theo cột của nhãn dương. Recall chia theo hàng.

> **check** Lời giải
> **A.** Chọn lớp 0. TP = 3, FP = 1, FN = 3. Precision = 3/4 = 0,75 và recall = 3/6 = 0,50.
