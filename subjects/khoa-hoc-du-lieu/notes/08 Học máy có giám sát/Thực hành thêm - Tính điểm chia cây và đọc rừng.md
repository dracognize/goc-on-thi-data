# Thực hành thêm · Tính điểm chia cây và đọc rừng

## Cây hồi quy: chấm một ngưỡng trước khi chia

Dùng số năm kinh nghiệm $x=(1,2,3,4)$ và lương $y=(10,14,30,36)$ triệu. Thử chia theo ngưỡng $x\leq 2{,}5$. Hai nhánh là lá nếu dừng ở độ sâu 1. Mỗi lá dự đoán bằng trung bình của các mẫu huấn luyện đi vào lá đó.



> **note** Bảng dạng chữ
> | Nhánh | Mẫu | Dự đoán | Sai số bình phương từng mẫu |
> | --- | --- | ---: | --- |
> | $x\leq 2{,}5$ | 10, 14 | 12 | 4 và 4 |
> | $x>2{,}5$ | 30, 36 | 33 | 9 và 9 |

Điểm MSE có trọng số sau chia là $(4+4+9+9)/4=6{,}5$, đơn vị bình phương triệu đồng. Nếu chia tại 3,5, lá trái dự đoán 18, lá phải dự đoán 36. Khi đó MSE là $(64+16+144+0)/4=56$. Thử cả các ngưỡng hợp lệ và chọn điểm thấp nhất ở nút đang xét. Lec 8 · Chọn ngưỡng cây hồi quy

```python
import numpy as np
from sklearn.tree import DecisionTreeRegressor

X = np.array([[1], [2], [3], [4]])
y = [10, 14, 30, 36]
tree = DecisionTreeRegressor(max_depth=1, random_state=5).fit(X, y)
assert np.isclose(tree.tree_.threshold[0], 2.5)
assert np.allclose(tree.predict([[1.5], [3.5]]), [12, 33])
```

`threshold[0]` là ngưỡng nút gốc. Khi dự đoán 1,5 hoặc 3,5, chỉ đi theo tiêu chí của các nút đã học. Điểm 6,5 bên trên được tính trên mẫu dùng để tạo nút. Dùng tập đánh giá riêng để ước lượng sai số trên dữ liệu mới.

## Cây phân loại: đọc độ thuần bằng Gini

Với nút có nhãn `[0,1,0,1,1]`, tỷ lệ lớp 0 là $2/5$, lớp 1 là $3/5$. Gini của nút là $1-(2/5)^2-(3/5)^2=0{,}48$. Một ngưỡng thử đưa `[0,1,0]` sang trái và `[1,1]` sang phải. Gini trái là $4/9$, phải bằng 0. Gini có trọng số sau chia là $(3/5)(4/9)+(2/5)0=4/15$. Nút bên phải thuần vì mọi hàng có cùng nhãn. Cây chọn ngưỡng giảm độ hỗn tạp nhiều ở nút hiện tại. Lec 8 · Chia cây phân loại

## Rừng: kết hợp dự đoán qua các cây

Rừng ngẫu nhiên thường tạo các cây từ những mẫu lấy có hoàn lại và thử một tập đặc trưng ở nút. Ví dụ nếu ba cây hồi quy dự đoán 20, 24 và 28 triệu, rừng dự đoán $(20+24+28)/3=24$ triệu. Với phân loại trong scikit-learn, rừng lấy trung bình xác suất lớp qua các cây rồi chọn lớp có xác suất trung bình lớn nhất.

```python
import numpy as np
from sklearn.ensemble import RandomForestClassifier, RandomForestRegressor

X = np.array([[1], [2], [3], [4], [5], [6]])
query = np.array([[2.5], [5.0]])

reg = RandomForestRegressor(n_estimators=5, max_depth=2, random_state=5)
reg.fit(X, [10, 14, 19, 23, 26, 31])
tree_outputs = [estimator.predict(query) for estimator in reg.estimators_]
assert np.allclose(reg.predict(query), np.mean(tree_outputs, axis=0))

clf = RandomForestClassifier(n_estimators=5, max_depth=2, random_state=5)
clf.fit(X, [0, 0, 1, 0, 1, 1])
tree_probs = [estimator.predict_proba(query) for estimator in clf.estimators_]
avg_probs = np.mean(tree_probs, axis=0)
assert np.allclose(clf.predict_proba(query), avg_probs)
assert np.array_equal(clf.predict(query), clf.classes_[avg_probs.argmax(axis=1)])
```

Cột xác suất đi theo thứ tự `classes_`. Tìm lớp dương theo nhãn trước khi lấy cột để vẽ ROC. Lec 8 · Rừng hồi quy · Rừng phân loại

## Điều kiện dừng và chuẩn hóa



> **note** Bảng dạng chữ
> | Họ | Việc làm lúc fit | Dừng hoặc kiểm soát phức tạp | Thang đo |
> | --- | --- | --- | --- |
> | KNN | Lưu mẫu và thiết lập cách tìm hàng xóm | Chọn số hàng xóm khi dự đoán | Khoảng cách dễ bị đặc trưng có thang lớn lấn át |
> | Cây | Chọn điều kiện chia tại từng nút | *`max_depth`*, `min_samples_leaf`, hoặc không còn cách chia hợp lệ | Biến đổi đơn điệu giữ thứ tự thường ít ảnh hưởng tới cách chia |
> | Rừng | Huấn luyện nhiều cây | *`n_estimators`* là số cây, đặt giới hạn từng cây riêng | Thường ít nhạy với thang đo tương tự cây |
> | Logistic Regression | Tối ưu hệ số | Hội tụ theo dung sai hoặc đạt `max_iter` | Thang tương đồng có thể hỗ trợ ổn định việc tối ưu và áp dụng điều chuẩn |
> | Linear Regression | Tìm hệ số giảm sai số bình phương | Cách dừng tùy thuật toán. Bộ giải bình phương tối thiểu có thể giải trực tiếp | Thang đo ảnh hưởng hệ số, diễn giải và độ ổn định số |

Ví dụ với KNN, chênh 1 năm kinh nghiệm nhưng chênh 1.000.000 đồng thu nhập. Nếu tính khoảng cách theo số gốc, thành phần thu nhập gần như quyết định kết quả. Dùng pipeline **`StandardScaler()`** rồi KNN giúp fit thang trên train và áp dụng cùng phép biến đổi cho mọi tập.

> **question** Nếu tăng số cây từ 5 lên 50, độ sâu từng cây có tự tăng?
> Không. *`n_estimators`* đổi số cây. *`max_depth`* là thiết lập độ sâu từng cây. Nếu thử nhiều giá trị, dùng validation hoặc cross-validation, rồi đánh giá cuối trên test.

Lec 8 · Điều kiện dừng · Chuẩn hóa dữ liệu · Về mục lục Lec 8
