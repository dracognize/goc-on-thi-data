# Công thức và cú pháp · Chương 08

> **abstract** Tóm tắt
> Bảng tra nhanh mọi công thức (MSE, RMSE, MAE, R², Sigmoid, Gini, Precision, Recall, F1, FPR), mọi lớp mô hình, thuộc tính sau **`fit`** và mẫu vẽ xuất hiện trong slide 8. Giải thích từng công thức nằm ở [03 Chương 08 - Hồi quy và KNN](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md), [04 Chương 08 - Logistic cây và rừng](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md), [05 Chương 08 - Ma trận nhầm lẫn và chỉ số](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md).

| Đại lượng | Công thức | Điều kiện hoặc cách đọc |
| --- | --- | --- |
| MAE | $\frac1n\sum_i\lvert y_i-\hat y_i\rvert$ | $n>0$, cùng đơn vị với đích |
| MSE | $\frac1n\sum_i(y_i-\hat y_i)^2$ | Đơn vị bình phương |
| RMSE | $\sqrt{\frac1n\sum_i(y_i-\hat y_i)^2}$ | Cùng đơn vị với đích |
| Hệ số xác định | $R^2=1-\frac{\sum_i(y_i-\hat y_i)^2}{\sum_i(y_i-\bar y)^2}$ | Công thức cần biến thiên đích |
| Khoảng cách Euclid | $d(x,z)=\sqrt{\sum_j(x_j-z_j)^2}$ | Đặc trưng phải so được về thang đo |
| Sigmoid | $p=1/(1+e^{-z})$ | So với ngưỡng trong phân loại nhị phân |
| Gini | $1-\sum_c p_c^2$ | $p_c$ là tỷ lệ lớp $c$ trong nút |
| Gini sau chia | $\frac{n_L}{n}G_L+\frac{n_R}{n}G_R$ | Ưu tiên mức giảm lớn hơn |
| Accuracy | $(TP+TN)/(TP+TN+FP+FN)$ | Mẫu đánh giá khác rỗng |
| Precision | $TP/(TP+FP)$ | Mẫu số là số dự đoán dương |
| Recall | $TP/(TP+FN)$ | Mẫu số là số dương thật |
| F1 | $2TP/(2TP+FP+FN)$ | Xác định khi mẫu số khác 0 |
| FPR | $FP/(FP+TN)$ | Mẫu số là số âm thật |
| MSE sau chia (cây hồi quy) | $\frac{n_L}{n}\text{MSE}_L+\frac{n_R}{n}\text{MSE}_R$ | Chọn ngưỡng cho giá trị nhỏ nhất |
| Ranh giới Logistic | $x^*=-\beta_0/\beta_1$ | Nơi $P=0.5$ |
| Entropy (Mở rộng) | $-\sum_c p_c\log_2p_c$ | 0 khi thuần, 1 khi 50/50 |

## Bảng tra API theo bước

[![C8 06 Chương 08 - Công thức và cú pháp – bảng 1](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Bước | API | Nhận gì | Kết quả hoặc tác động |
> | --- | --- | --- | --- |
> | Chia mẫu | **`train_test_split(X, y, test_size=0.25, random_state=42)`** | X và y có cùng số hàng | 4 kết quả theo thứ tự X train, X test, y train, y test |
> | Học biến đổi | **`scaler.fit(X_train)`** | Đặc trưng train | Lưu thống kê vào đối tượng scaler |
> | Áp dụng biến đổi | **`scaler.transform(X_test)`** | Đặc trưng test cùng cột và thứ tự | Dữ liệu test đã đổi với thống kê train |
> | Học dự đoán | **`model.fit(X_train, y_train)`** | Một hàng đặc trưng và một đích tương ứng trên mỗi mẫu | Cập nhật trạng thái mô hình |
> | Dự đoán nhãn hoặc số | **`model.predict(X_test)`** | Bảng đặc trưng test | Một dự đoán cho mỗi hàng |
> | Đọc xác suất lớp | **`model.predict_proba(X_test)`** | Mô hình phân loại có hỗ trợ | Mỗi hàng chứa xác suất theo thứ tự **`model.classes_`** |
> | Đếm đúng/sai theo lớp | **`confusion_matrix(y_test, pred, labels=[0,1])`** | Nhãn thật và dự đoán | Hàng thật, cột dự đoán theo thứ tự đã chọn |
> | Tính MAE | **`mean_absolute_error(y_test, pred)`** | Hai dãy số ghép theo mẫu | Một số theo đơn vị của đích |

**Giải ký hiệu trước khi bấm máy.** $i$ đánh số từng mẫu, $n$ là số mẫu và ký hiệu $\sum_i$ nghĩa là cộng kết quả của từng mẫu. Với giá thật $[10,20]$ và dự đoán $[12,16]$, ghép theo mẫu: hiệu lần lượt $-2$ và $4$. MAE lấy độ lớn 2 và 4 rồi chia 2, bằng 3. MSE lấy bình phương 4 và 16 rồi chia 2, bằng 10. RMSE lấy căn 10, xấp xỉ 3,162. Lấy căn ở cuối để trở lại đơn vị đầu.

**Tra nhanh scikit-learn.** Chia bằng train_test_split, fit trên train rồi dùng predict dự đoán. Với ROC, truyền điểm hoặc xác suất lớp dương phù hợp từ predict_proba. Với regression, tính np.sqrt(mean_squared_error(y_test, pred)). Chỉ định thứ tự nhãn nếu cần bảo đảm cách đọc confusion_matrix.

**Ví dụ.** Sai số tuyệt đối là 1 và 3 thì MAE=2, MSE=5, RMSE xấp xỉ 2.236.

## Lớp mô hình trong slide

Nguồn: tr. 26, tr. 61

[![C8 06 Chương 08 - Công thức và cú pháp – bảng 2](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.svg)](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.md)

> **note** Bảng dạng chữ
> | Module | Lớp | Tham số dùng trong slide | Bài toán |
> | --- | --- | --- | --- |
> | **`sklearn.linear_model`** | **`LinearRegression()`** | (không) | Hồi quy |
> | **`sklearn.linear_model`** | **`LogisticRegression(random_state=42)`** | `max_iter` là điều kiện dừng | Phân loại |
> | **`sklearn.neighbors`** | **`KNeighborsRegressor(n_neighbors=3)`** / **`KNeighborsClassifier(n_neighbors=3)`** | *`n_neighbors`* = K | Hồi quy / phân loại |
> | **`sklearn.tree`** | **`DecisionTreeRegressor(max_depth=1, random_state=42)`** / **`DecisionTreeClassifier(...)`** | *`max_depth`*, `min_samples_split` | Hồi quy / phân loại |
> | **`sklearn.ensemble`** | **`RandomForestRegressor(random_state=42, n_estimators=3)`** / **`RandomForestClassifier(...)`** | *`n_estimators`* = số cây | Hồi quy / phân loại |
> | **`sklearn.tree`** | **`plot_tree(model, feature_names=[...], class_names=[...], filled=True, rounded=True, precision=2)`** | `ax=` để vẽ vào ô subplot | Vẽ cây |
> | **`sklearn.metrics`** | **`mean_squared_error`**, **`accuracy_score`**, **`roc_curve`**, **`roc_auc_score`** | | Đánh giá |

## Thuộc tính sau `fit` và kết quả in ra trong slide

[![C8 06 Chương 08 - Công thức và cú pháp – bảng 3](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.svg)](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.md)

> **note** Bảng dạng chữ
> | Thuộc tính / lệnh | Ý nghĩa | Giá trị trong slide |
> | --- | --- | --- |
> | `model_lr.coef_[0]`, `model_lr.intercept_` | $\beta_1$, $\beta_0$ của Linear | 4.8232; 10.1923 |
> | `model_log_reg.coef_[0][0]`, `model_log_reg.intercept_[0]` | $\beta_1$, $\beta_0$ của Logistic (mảng 2 chiều / mảng) | 1.1590; −5.5288 |
> | `-intercept_ / coef_[0]` | Ranh giới quyết định Logistic ($P=0.5$) | ≈ 4.77 |
> | `model.predict_proba(X)[:, 1]` | Xác suất lớp 1 | 0.29 ($x=4$); 0.99 ($x=9$) |
> | `model_dt_cls.tree_.threshold[0]` | Ngưỡng nút gốc của cây | 5.0 (phân loại); 4.5 (hồi quy) |
> | `model_rf.estimators_` | Danh sách các cây con trong rừng | 3 cây |
> | **`np.sqrt(mean_squared_error(y_test, preds))`** | RMSE | Linear 2.3951; KNN/cây/rừng 12.0208 |
> | **`accuracy_score(y_test, preds)`** | Accuracy | 1.00 cho cả 4 mô hình phân loại |
> | **`roc_auc_score(y_test, proba)`** | AUC | 1.0000 |

## Mẫu vẽ lặp lại trong slide

[![C8 06 Chương 08 - Công thức và cú pháp – bảng 4](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.svg)](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2006%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.md)

> **note** Bảng dạng chữ
> | Lệnh | Vai trò |
> | --- | --- |
> | **`plt.scatter(X, y, color=..., marker='x', s=100, label=...)`** | Điểm train / test thật / test dự đoán |
> | `X_plot = np.linspace(0, 10, 100).reshape(-1, 1)` rồi **`model.predict(X_plot)`** | Vẽ đường dự đoán liên tục |
> | **`plt.axvline(x=...)`**, **`plt.axhline(y=0.5)`** | Ranh giới quyết định, mức xác suất 0.5 |
> | **`np.diff(y_plot)`** và `X_plot[:-1][diff != 0]` | Tìm chỗ nhãn dự đoán đổi (ranh giới KNN, rừng) |
> | **`plt.bar(models, rmses)`**, **`plt.ylim(...)`**, **`plt.text(i, v + 0.2, f"{v:.2f}", ha='center')`** | Biểu đồ cột so sánh mô hình |
> | `fig, axes = plt.subplots(nrows=1, ncols=3, figsize=(20, 8))` | Vẽ 3 cây của rừng cạnh nhau |
> | **`plt.savefig('ml_image1.png')`** | Lưu hình |

Nguồn Chỉ số, tr. 100, tr. 105, tr. 107, KNN, Gini, Chỉ số nâng cao.
