# Scale theo thống kê đã học

**Lý thuyết.** [Chuẩn hóa dữ liệu](../../05%20L%C3%A0m%20s%E1%BA%A1ch/03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) · [Bảng tra chương 5](../../05%20L%C3%A0m%20s%E1%BA%A1ch/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Xác định scaler và lần `fit` còn hiệu lực. Tách mốc trừ, mẫu số và trường hợp `transform` dùng thông số đã học.

## Ví dụ có lời giải

Ví dụ mới: fit MinMaxScaler trên 10 và 30. Dùng scaler này transform 25 để được `(25−10)/(30−10)=0.75`. Dùng đúng scaler transform 40 để được 1.5 với chế độ mặc định.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Chi phí quảng cáo của các chiến dịch có giá trị nhỏ nhất là 10 triệu đồng và lớn nhất là 50 triệu đồng. Sau khi chuẩn hóa Min-Max về [0, 1], chiến dịch có chi phí 30 triệu đồng nhận giá trị nào?

- **A.** 0.4
- **B.** 0.5
- **C.** 0.75
- **D.** 0.6

> **tip** Gợi ý
> Khoảng mới là [0,1], nên chia theo khoảng giá trị gốc.

> **success** Đáp án B
> $(30-10)/(50-10)=0.5$.

Nguồn ScoreUp, nhóm 5, ID `Q01954`.

### 2 · Vận dụng

Cột Gia (triệu VND) gồm 10, 20, 30, 40 và 1000 được chuẩn hóa bằng RobustScaler. Hai giá trị in ra lần lượt là điểm của dòng cuối rồi dòng đầu. Kết quả là gì?

```python
import pandas as pd
from sklearn.preprocessing import RobustScaler

df = pd.DataFrame({'Gia': [10, 20, 30, 40, 1000]})
scaled = RobustScaler().fit_transform(df'Gia')
print(scaled[4, 0])
print(scaled[0, 0])
```

- **A.** 48.5 và -1.0, vì trung vị là 30 và IQR = Q3 - Q1 = 40 - 20 = 20 nên giá trị 1000 ra (1000 - 30) / 20
- **B.** 39.0 và -10.5, vì mốc trừ là giá trị trung bình 220 còn mẫu số vẫn là IQR bằng 20 như trong công thức
- **C.** 50.0 và 0.5, vì dữ liệu được chia cho IQR bằng 20 mà quên trừ đi trung vị ở tử số của công thức
- **D.** 0.98 và -0.02, vì mẫu số là khoảng max - min bằng 990 trong khi mốc trừ vẫn là trung vị bằng 30

> **tip** Gợi ý
> Tìm trung vị và hai tứ phân vị trước khi thay x.

> **success** Đáp án A
> Trung vị 30, $Q_1=20$, $Q_3=40$. Điểm của 1000 là 48.5 và điểm của 10 là −1.0.

Nguồn ScoreUp, nhóm 5, ID `Q01930`.

### 3 · Tổng hợp

Một nhà phân tích dùng cùng một đối tượng MinMaxScaler tên sc để fit_transform lần lượt cột so_don rồi cột chi_phi, sau đó gọi sc.transform cho giá trị 10. Giá trị in ra là gì và dựa trên tham số nào?

```python
import numpy as np
from sklearn.preprocessing import MinMaxScaler

so_don = np.array([[0.0], [50.0], [100.0]])
chi_phi = np.array([[0.0], [10.0], [20.0]])
sc = MinMaxScaler()
a = sc.fit_transform(so_don)
b = sc.fit_transform(chi_phi)
print(sc.transform(np.array(10.0))[0][0])
```

- **A.** 0.1, theo min và max của so_don đã fit trước đó
- **B.** 0.0, do scaler fit lại trên chính giá trị 10
- **C.** Báo lỗi, vì scaler không cho fit lại lần hai
- **D.** 0.5, theo min và max của chi_phi đã fit sau cùng

> **tip** Gợi ý
> Một lần fit mới ghi đè trạng thái đã học lần trước.

> **success** Đáp án D
> Lần `fit_transform` thứ hai dùng biên 0 và 20. `transform` dùng biên này để cho $(10-0)/(20-0)=0.5$.

Nguồn ScoreUp, nhóm 5, ID `Q01923`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
