# Tiền xử lý và rò rỉ

**Cần biết trước.** [Chương 08 - Train test và rò rỉ](../../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md).

**Quy trình giải.** Kiểm tra mẫu nào tham gia ước lượng trung bình, độ lệch chuẩn hoặc giá trị điền. Chia tập trước, fit trên train và dùng transformer đã fit để transform test.

Làm từng bài trước khi mở gợi ý, rồi so sánh quy tắc với bài trước.

## 1 · Cơ bản

Khi chuẩn hóa dữ liệu bằng StandardScaler trước khi huấn luyện KNeighborsRegressor, cách nào đúng để tránh rò rỉ thông tin từ tập test?

- **A.** Fit StandardScaler trên toàn bộ dữ liệu (cả train lẫn test) rồi mới chia train/test
- **B.** Fit StandardScaler trên X_train, rồi dùng chính scaler đó transform cho cả X_train và X_test
- **C.** Fit một StandardScaler riêng trên X_test, rồi transform X_test để cùng thang đo với dữ liệu thật
- **D.** Bỏ bước chuẩn hóa, vì KNeighborsRegressor tự chuẩn hóa dữ liệu khi gọi fit

ID ScoreUp: `Q03457`

> **hint** Gợi ý 1
> Xác định khái niệm hoặc quy tắc được hỏi.

> **hint** Gợi ý 2
> Kiểm tra mẫu nào tham gia ước lượng trung bình, độ lệch chuẩn hoặc giá trị điền. Chia tập trước, fit trên train và dùng transformer đã fit để transform test.

> **check** Bài mẫu giải đầy đủ
> **B.** Fit StandardScaler trên train, dùng cùng scaler để transform test.

## 2 · Vận dụng

Cột thu_nhap của bảng khách hàng bị thiếu giá trị ở một số dòng. Nhóm muốn điền giá trị thiếu bằng trung bình của cột rồi chuẩn hóa bằng StandardScaler trước khi huấn luyện KNN. Quy trình nào đúng và không để thông tin từ tập test rò rỉ vào quá trình huấn luyện?

- **A.** Tính trung bình trên toàn bộ dữ liệu để điền thiếu, chia train/test, fit scaler trên train, transform cả hai rồi huấn luyện
- **B.** Chia train/test, tính trung bình từ train để điền thiếu cho cả hai tập, fit scaler trên train, transform cả hai rồi huấn luyện
- **C.** Chia train/test, điền thiếu mỗi tập bằng trung bình riêng của tập đó, fit_transform scaler riêng trên từng tập rồi huấn luyện KNN
- **D.** Chuẩn hóa toàn bộ dữ liệu bằng fit_transform, chia train/test, điền thiếu bằng trung bình của tập train rồi huấn luyện KNN

ID ScoreUp: `Q03626`

> **hint** Gợi ý 1
> Gạch dữ kiện có ảnh hưởng đến kết quả.

> **hint** Gợi ý 2
> Kiểm tra mẫu nào tham gia ước lượng trung bình, độ lệch chuẩn hoặc giá trị điền. Chia tập trước, fit trên train và dùng transformer đã fit để transform test.

> **check** Lời giải
> **B.** Cả thống kê điền thiếu và chuẩn hóa phải học từ train, rồi áp dụng tuần tự cho test.

## 3 · Vận dụng mở rộng

Đoạn code sau có một lỗi khiến việc chuẩn hóa dữ liệu không đúng cách (gây rò rỉ dữ liệu). Dòng nào là dòng có vấn đề?


```python
X_train = np.array([[1.0], [2.0], [3.0]])
X_test = np.array([[4.0], [5.0]])

mean_train = X_train.mean()
std_train = X_train.std()

X_train_scaled = (X_train - mean_train) / std_train
X_test_scaled = (X_test - X_test.mean()) / X_test.std()

print(X_train_scaled.shape, X_test_scaled.shape)
```
- **A.** X_test_scaled = (X_test - X_test.mean()) / X_test.std()
- **B.** X_train_scaled = (X_train - mean_train) / std_train
- **C.** print(X_train_scaled.shape, X_test_scaled.shape)
- **D.** `X_train = np.array([[1.0], [2.0], [3.0]])`

ID ScoreUp: `Q03780`

> **hint** Gợi ý 1
> Viết trạng thái trung gian hoặc xác định tác động của từng thao tác.

> **hint** Gợi ý 2
> Kiểm tra mẫu nào tham gia ước lượng trung bình, độ lệch chuẩn hoặc giá trị điền. Chia tập trước, fit trên train và dùng transformer đã fit để transform test.

> **check** Lời giải
> **A.** Dòng tính mean và std ngay trên X_test làm thống kê tiền xử lý phụ thuộc vào tập test. Dùng mean_train và std_train để transform test.
