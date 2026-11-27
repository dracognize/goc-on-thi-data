# Tự kiểm tra · Chương 08

> **abstract** Tóm tắt
> Mở từng câu sau khi tự trả lời. Phần đầu luyện suy luận; phần "Theo đúng số liệu slide" kiểm tra các con số hay ra thi.

> **question** Dự đoán giá nhà và dự đoán nhóm giá được học theo bài toán gì?
> Giá cụ thể là hồi quy. Nhóm giá được định nghĩa sẵn và có nhãn là phân loại.

> **question** Dùng k=3, ba hàng gần nhất mang nhãn A, B, B và đích số 12, 18, 24. Kết quả là gì?
> Với trọng số đều, phân loại chọn B. Hồi quy dự đoán 18.

> **question** Cho TP=12, FP=8, FN=4, TN=76. Precision, Recall và F1?
> Precision là 0.6, Recall 0.75 và F1 khoảng 0.667.

> **question** Với đích dự báo 10 và 20, mô hình dự báo 12 và 16. MAE và RMSE?
> MAE là 3. MSE là 10 nên RMSE xấp xỉ 3.162.

> **question** Dùng toàn bộ dữ liệu để fit scaler rồi mới chia train/test gây vấn đề gì?
> Tham số scaler đã nhận thông tin từ test. Chia trước, fit scaler trên train và transform test bằng tham số đã fit.

> **question** Mô hình học từ bảng 20 hàng và 3 cột đặc trưng. Cần truyền gì để dự đoán một hàng mới?
> Truyền bảng một hàng ba cột cùng thứ tự và kiểu đặc trưng. Không cần nhãn thật lúc dự đoán.

> **question** Nếu khoảng cách từ query đến các mẫu có đích 7, 12, 20 lần lượt là 1, 3, 2 thì KNN hồi quy k=2 dự đoán gì?
> Sắp khoảng cách 1, 2, 3. Lấy đích 7 và 20 rồi tính trung bình, bằng 13,5.

> **question** Mô hình cho xác suất lớp dương 0,62. Dự đoán nhãn khi dùng ngưỡng 0,5 rồi 0,7 là gì?
> Dương với ngưỡng 0,5 và âm với 0,7. Đổi ngưỡng chỉ đổi quyết định trên xác suất đó.

> **question** Tập validation cho điểm cao khi k=3, nhưng tập test giảm mạnh. Nên kiểm tra gì trước?
> Kiểm tra cách chia, sự khác biệt dữ liệu và việc có chọn quá nhiều lần theo validation hay không. Giữ tập test độc lập khi chọn lại cấu hình.

**Bài làm.** Tự tạo 8 điểm 2D có nhãn A/B. Chọn một query và tính khoảng cách, dự đoán bằng KNN, sau đó so với dự đoán sau chuẩn hóa. Giải thích vì sao láng giềng thay đổi hoặc giữ nguyên.

## Theo đúng số liệu slide

> **question** Loại học máy nào dùng phần thưởng và hình phạt? Loại nào phân cụm khách hàng? (tr. 9)
> Học củng cố (Reinforcement Learning). Phân cụm khách hàng là học không giám sát.

> **question** Theo slide, tập train và test thường chiếm bao nhiêu phần trăm? (tr. 13)
> Train 70–80%, test 20–30%.

> **question** Mô hình dùng đường thẳng cho dữ liệu dạng parabol gặp hiện tượng gì? Khắc phục? (tr. 17)
> Dưới khớp. Dùng mô hình phức tạp hơn, thêm đặc trưng.

> **question** Linear Regression slide: Lương ≈ 10.19 + 4.82 × Kinh nghiệm. Tính RMSE trên hai điểm test (7, 45) và (8, 52). (tr. 29)
> Dự đoán 43.95 và 48.78. RMSE $=\sqrt{(1.05^2+3.22^2)/2}\approx2.395$.

> **question** Cây hồi quy chọn ngưỡng nào ở gốc và vì sao? Lá phải dự đoán bao nhiêu? (tr. 41)
> Kinh nghiệm < 4.5, vì MSE sau chia nhỏ nhất (15.40). Lá phải $(35+36+40)/3=37$.

> **question** Vì sao KNN, cây và rừng có cùng RMSE 12.0208 còn Linear chỉ 2.3951? (tr. 54)
> Ba mô hình đều trả trung bình nhóm {5; 5.5; 6} = 37, không ngoại suy được cho $x=7,8$. Đường thẳng thì kéo dài được xu hướng tăng.

> **question** Logistic với $\beta_0=-5.5288$, $\beta_1=1.1590$: xác suất Đạt khi học 4 giờ? Ranh giới quyết định? (tr. 64)
> $1/(1+e^{0.8928})\approx0.29$ → Trượt. Ranh giới $5.5288/1.1590\approx4.77$ giờ.

> **question** Gini nút gốc 4 Trượt / 4 Đạt? Ngưỡng tối ưu và Gini sau chia? (tr. 77)
> 0.5. Ngưỡng 5.0 cho Gini sau chia 0.0.

> **question** Ba nhóm mô hình và điều kiện dừng của chúng? (tr. 95)
> Linear/Logistic: `max_iter` hoặc cải thiện rất nhỏ. Cây: nút thuần, *`max_depth`*, `min_samples_split`. KNN: không có (học lười).

> **question** Mô hình nào cần chuẩn hóa dữ liệu? (tr. 97)
> KNN, Linear, Logistic. Cây và rừng không cần.

> **question** Trong ma trận nhầm lẫn của slide, lỗi loại I và loại II là ô nào? (tr. 104)
> Loại I = FP (báo động giả). Loại II = FN (bỏ sót).

> **question** AUC của Logistic trên 2 điểm test bằng bao nhiêu? Đoán ngẫu nhiên có AUC bao nhiêu? (tr. 107)
> 1.0000. Đoán ngẫu nhiên 0.5.

Ôn bằng thẻ: Thẻ nhớ chương 8.
