# Bốn ca học máy trong lecture

> **abstract** Tóm tắt
> | Ca | Trang | Mục tiêu $y$ | Loại | Mô hình | Kết quả slide |
> | --- | --- | --- | --- | --- | --- |
> | Quảng cáo 55 cửa hàng | 90–98 | Sales (tỷ đồng) | Hồi quy | Hồi quy tuyến tính | Flyer không ý nghĩa → bỏ; TV, Social có ý nghĩa |
> | Hoa Iris 150 bông | 99–107 | Loài (3 lớp) | Phân loại | KNN | 49/50 = 98% |
> | Giá nhà Hà Nội | 108–115 | Giá (triệu/m²) | Hồi quy | Rừng ngẫu nhiên | MAE ≈ 27,88; R² ≈ 0,46 |
> | Gửi tiết kiệm ngân hàng | 116–123 | term_deposit 0/1 | Phân loại nhị phân | Hồi quy logistic | 484/2000 đồng ý (24,2%) so với ~186 ngẫu nhiên |

Mục lục phần 1.4 (tr. 87): 1.4.1 giới thiệu học máy (xem [03 Nhãn và loại bài toán](03%20Nh%C3%A3n%20v%C3%A0%20lo%E1%BA%A1i%20b%C3%A0i%20to%C3%A1n.md)); 1.4.2–1.4.5 là bốn ca dưới đây.

Chọn **đầu ra** trước khi chọn thuật toán. **Đặc trưng** là thông tin có sẵn đưa vào mô hình. **Biến mục tiêu** là thông tin cần dự đoán. Trong ký hiệu `X` và *`y`*, `X` có một hàng cho mỗi quan sát, *`y`* có một giá trị mục tiêu cho mỗi hàng.

## 1. Tối ưu hóa ngân sách quảng cáo

### Bài toán và dữ liệu

Nguồn tr. 90, tr. 91.

Công ty có dữ liệu **55 cửa hàng**, 3 kênh: **TV, mạng xã hội, tờ rơi**. Năm câu hỏi:
1. Liên hệ chi phí quảng cáo – doanh thu mạnh đến đâu?
2. Kênh nào đóng góp nhiều nhất?
3. Tác động có **tuyến tính** không?
4. Có **tương tác** giữa các kênh không?
5. Phân bổ ngân sách thế nào là **tối ưu**?

- Biến mục tiêu: **Sales** (tỷ đồng).
- Biến độc lập: **TV, Social_Media, Flyer** (triệu đồng).

### Trực quan hóa

Nguồn tr. 92, tr. 93.

- Trang 92: ba biểu đồ phân tán *TV / Mạng xã hội / Tờ rơi vs Doanh thu*, cả ba đều có đường xu hướng **dốc lên**.
- Trang 93: các kênh có liên hệ với nhau không? *TV vs Flyer* và *Flyer vs Mạng xã hội* dốc lên rõ; *Mạng xã hội vs TV* gần như phẳng.

> **info** Mở rộng: vì sao tờ rơi "tốt" trên biểu đồ nhưng không có ý nghĩa trong mô hình?
> Flyer tăng cùng TV (tr. 93). Khi đứng một mình, Flyer "mượn" ảnh hưởng của TV nên biểu đồ dốc lên. Khi TV và Social đã nằm trong mô hình, phần riêng của Flyer gần như không còn. Hiện tượng các biến giải thích tương quan với nhau gọi là **đa cộng tuyến**.

### Mô hình

Nguồn tr. 94–tr. 96.

Xây mô hình = ước lượng hàm $f$:

$$\text{Sales} = f(\text{TV}, \text{SocialMedia}, \text{Flyer}) + \epsilon$$

- Sales: **biến phụ thuộc**; TV, SocialMedia, Flyer: **biến giải thích** (inputs).
- $\epsilon$: **sai số ngẫu nhiên**, các yếu tố không đo được.
- Mục tiêu: ước lượng $f$ từ dữ liệu; **định lượng tác động từng kênh**.

Sales **liên tục** → **hồi quy**; bối cảnh hỗ trợ quyết định kinh tế → mô hình **có tham số**.

[![C1 Bốn ca học máy trong lecture – bảng 1](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Mô hình | Ưu điểm | Hạn chế |
> | --- | --- | --- |
> | Hồi quy tuyến tính | Dễ hiểu, dễ triển khai, giải thích rõ | Giả định quan hệ tuyến tính |
> | Cây quyết định hồi quy | Mô tả phi tuyến, trực quan, dễ giải thích | Dễ **overfit** nếu không kiểm soát |
> | Rừng ngẫu nhiên (RF) | Chính xác, giảm overfit so với cây đơn | Khó giải thích từng đặc trưng |
> | Gradient boosting (GB; slide gọi "học tăng cường") | Rất chính xác, tốt cho dữ liệu phức tạp | Khó triển khai & giải thích |

**Kết luận chọn**: dữ liệu nhỏ + ưu tiên giải thích → **hồi quy tuyến tính**.

> **warning** Dễ nhầm thuật ngữ
> Slide dịch *gradient boost* là "học tăng cường", trùng tên với *reinforcement learning* (học tăng cường ở tr. 89). Trong câu hỏi về **loại bài toán**, "học tăng cường" = reinforcement. Trong **danh sách mô hình hồi quy/phân loại**, đó là gradient boosting.

### Hệ số và kiểm định

Nguồn tr. 97, tr. 98.

$$f = \beta_0 + \beta_1 \cdot \text{TV} + \beta_2 \cdot \text{SocialMedia} + \beta_3 \cdot \text{Flyer}$$

Ước lượng bằng **Sklearn**:

$$\text{Sales} = 4.09 + 0.016\,\text{TV} + 0.063\,\text{SocialMedia} + 0.012\,\text{Flyer}$$

- Hệ số **0.012** của Flyer **không có ý nghĩa thống kê** → tờ rơi không ảnh hưởng rõ rệt.
- Bỏ Flyer, ước lượng lại: $\text{Sales} = 4.09 + 0.019\,\text{TV} + 0.070\,\text{SocialMedia}$. Cả hai hệ số **có ý nghĩa**.
- Kết luận: TV và Social **tác động tích cực, đáng kể**; Flyer không hiệu quả; dùng mô hình tuyến tính để **tìm phân bổ ngân sách tối ưu**.

> **example** Đọc hệ số (đã chạy kiểm chứng)
> ```python
> def du_bao(tv, social):
>     return 4.09 + 0.019 * tv + 0.070 * social
> print(round(du_bao(150, 25), 3))   # mốc
> print(round(du_bao(150, 26), 3))   # +1 triệu cho Social
> print(round(du_bao(151, 25), 3))   # +1 triệu cho TV
> ```
> ```text
> 8.69
> 8.76
> 8.709
> ```
> Thêm 1 triệu cho Social (giữ TV cố định) tăng dự báo **0,07 tỷ**; cho TV tăng **0,019 tỷ**. Social có hệ số lớn hơn nên mỗi triệu đồng hiệu quả hơn.

> **warning** Dễ nhầm
> Hệ số **nhỏ** ≠ **không có ý nghĩa**. Flyer bị loại vì **kiểm định** cho thấy không có ý nghĩa thống kê, không phải vì 0.012 nhỏ. TV có hệ số 0.016 còn nhỏ hơn mà vẫn giữ.

> **question** Tự kiểm tra: Sau khi bỏ Flyer, phương trình là gì? Vì sao bài toán này là hồi quy?
> $\text{Sales} = 4.09 + 0.019\,\text{TV} + 0.070\,\text{SocialMedia}$. Vì Sales là biến liên tục.

## 2. Phân loại hoa Iris

### Bài toán

Nguồn tr. 99, tr. 100.

Dự đoán loài **setosa, versicolor, virginica** từ 4 đặc trưng: chiều dài, rộng **cánh hoa** (petal) và **đài hoa** (sepal). Dữ liệu **150 bông**.

$$\text{Loài hoa} = f(\text{Cánh hoa (dài, rộng)}, \text{Đài hoa (dài, rộng)})$$

$f$ chỉ nhận 3 giá trị **0 (setosa), 1 (versicolor), 2 (virginica)** → $f$ là **mô hình phân loại**.

### Đánh giá: tập huấn luyện và tập kiểm tra

Nguồn tr. 101.

- **Tập huấn luyện (Training Set)**: xây và huấn luyện mô hình, học mối quan hệ.
- **Tập kiểm tra (Test Set)**: đánh giá trên **dữ liệu mới chưa thấy** → đo khả năng dự đoán thực tế.
- Chia phải **ngẫu nhiên**.

### Khám phá dữ liệu

Nguồn tr. 102, tr. 103. Mục đích: hiểu cấu trúc, quan hệ giữa biến; phát hiện bất thường.

Thống kê đơn giản theo loài (trung bình ± độ lệch chuẩn, [min–max]) trên slide:

[![C1 Bốn ca học máy trong lecture – bảng 2](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.svg)](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.md)

> **note** Bảng dạng chữ
> | Loài | Dài đài | Rộng đài | Dài cánh | Rộng cánh |
> | --- | --- | --- | --- | --- |
> | setosa | 5,047 ± 0,375 [4,3–5,8] | 3,481 ± 0,372 [2,9–4,4] | **1,464** ± 0,176 [1,0–1,9] | **0,236** ± 0,099 [0,1–0,5] |
> | versicolor | 5,948 ± 0,540 [4,9–7,0] | 2,767 ± 0,293 [2,2–3,2] | 4,209 ± 0,518 [3,0–5,1] | 1,318 ± 0,210 [1,0–1,8] |
> | virginica | 6,542 ± 0,651 [4,9–7,9] | 2,983 ± 0,322 [2,2–3,8] | 5,539 ± 0,535 [4,5–6,7] | 2,006 ± 0,291 [1,4–2,5] |

Biểu đồ phân tán *dài cánh vs rộng cánh* (tr. 103): **setosa tách hẳn** (góc dưới trái); versicolor và virginica **chồng lấn một phần** ở vùng dài cánh ≈ 4,5–5,1.

> **tip** Đọc bảng
> Dài cánh của setosa tối đa 1,9; của hai loài kia tối thiểu 3,0. Chỉ một ngưỡng "dài cánh < 2,5" đã tách được setosa. Nhầm lẫn nếu có sẽ nằm giữa versicolor và virginica.

### Chọn mô hình

Nguồn tr. 104. Mục tiêu phân loại → mô hình phân loại; cần chính xác → có tham số **hoặc phi tham số**. Ứng viên: **k-láng giềng gần nhất**, hồi quy logistic, cây quyết định phân loại, rừng ngẫu nhiên, gradient boosting.

### k-láng giềng gần nhất (KNN)

Nguồn tr. 105.

Với điểm mới:
1. Tính **khoảng cách** đến **mọi** điểm huấn luyện.
2. Chọn **k điểm gần nhất**.
3. Gán **nhãn chiếm đa số** trong k điểm đó.

[![C1 KNN bỏ phiếu](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20KNN%20b%E1%BB%8F%20phi%E1%BA%BFu.excalidraw.svg)](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20KNN%20b%E1%BB%8F%20phi%E1%BA%BFu.excalidraw.md)

> **example** Tính tay với một đặc trưng (số tự đặt)
> Hoa mới có số đo 2,9. Năm hoa đã biết:
>
> | Số đo | Nhãn | Khoảng cách tới 2,9 |
> | --- | --- | ---: |
> | 1,0 | setosa | 1,9 |
> | 1,5 | setosa | 1,4 |
> | 3,0 | versicolor | **0,1** |
> | 3,4 | versicolor | **0,5** |
> | 4,1 | virginica | **1,2** |
>
> $k=3$ → 3 điểm gần nhất: 3,0; 3,4; 4,1 → 2 versicolor, 1 virginica → **versicolor**. Với 4 đặc trưng, dùng khoảng cách Euclid $d=\sqrt{\sum_j (x_j - x'_j)^2}$ (Mở rộng).

### Ví dụ dự đoán và độ chính xác

Nguồn tr. 106, tr. 107.

Hoa mới với 4 số đo 5 / 2,9 / 1 / 0,2 → dự đoán **setosa**. Đánh giá **không dùng X_train** mà dùng **X_test**: đúng **49/50** → **98%**. Tập kiểm tra 50 trên 150 bông.

> **warning** Lỗi nhãn trên slide tr. 106
> Phần chữ ghi "chiều dài **cánh** hoa 5cm … chiều dài **đài** hoa 1cm". Bảng kết quả bên dưới lại xếp 5,0 vào cột *Chiều_dài_đài_hoa* và 1 vào *Chiều_dài_cánh_hoa*. Bảng kết quả hợp lý hơn: cánh dài 1 cm đúng là setosa (cánh setosa 1,0–1,9).

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
iris = load_iris()
X, y = iris.data, iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=50, random_state=0)
knn = KNeighborsClassifier(n_neighbors=5).fit(X_train, y_train)
moi = 5.0, 2.9, 1.0, 0.2   # dài đài, rộng đài, dài cánh, rộng cánh
print("Dự đoán:", iris.target_names[knn.predict(moi)][0])
print("Đúng:", (knn.predict(X_test) == y_test).sum(), "/", len(y_test))
print("Điểm tập kiểm tra:", knn.score(X_test, y_test))
```

```text
Dự đoán: setosa
Đúng: 49 / 50
Điểm tập kiểm tra: 0.98
```

> **info** Mở rộng
> Slide không ghi giá trị k và cách chia. Đoạn code trên dùng *`k=5`*, *`random_state=0`* và tái tạo đúng 49/50. Đổi *`random_state`* có thể cho 0,92–1,0, vì độ chính xác phụ thuộc cách chia ngẫu nhiên.

> **question** Tự kiểm tra: Vì sao không đánh giá bằng X_train?
> Mô hình đã thấy X_train nên điểm sẽ lạc quan. Cần dữ liệu chưa thấy (X_test) để đo khả năng dự đoán thực tế.

## 3. Dự đoán giá bất động sản Hà Nội

### Bài toán và làm sạch

Nguồn tr. 108, tr. 109.

Dự đoán **giá nhà (triệu đồng/m²)** từ: **vị trí** (quận, huyện); **tính chất nhà** (loại hình, số tầng, số phòng ngủ, diện tích…); **pháp lý** (giấy tờ).

Dữ liệu thực tế không hoàn hảo. Cột **Giá/m2 là chuỗi**, nhiều đơn vị (tỷ đồng, đồng) → **tách số và đơn vị** → quy về **triệu đồng/m²**. Bảng sau làm sạch có các cột: Địa chỉ, Quận, Huyện, Loại hình nhà ở, Giấy tờ pháp lý, Số tầng, Số phòng ngủ, Diện tích, Dài, Rộng, Giá/m2.

> **example** Chuẩn hóa đơn vị (Mở rộng, đã chạy)
> ```python
> def ve_trieu(chuoi):
>     so, dv = chuoi.split()
>     so = float(so.replace(",", "."))
>     return {"tỷ": so * 1000, "triệu": so, "đồng": so / 1e6}[dv]
> for s in ["1,2 tỷ", "95 triệu", "88000000 đồng"]:
>     print(s, "->", ve_trieu(s))
> ```
> ```text
> 1,2 tỷ -> 1200.0
> 95 triệu -> 95.0
> 88000000 đồng -> 88.0
> ```

### Trực quan hóa

Nguồn tr. 110, tr. 111.

- **Boxplot giá theo quận**: thấp nhất khoảng Hà Đông, Long Biên, Bắc Từ Liêm; cao nhất **Hoàn Kiếm** (hộp rộng, trung vị cao nhất). Nhiều điểm ngoại lai phía trên ở mọi quận.
- **Boxplot giá theo số tầng**: giá/m² **tăng theo số tầng**, rõ nhất từ 6 tầng trở lên.

### Chọn mô hình và đánh giá

Nguồn tr. 112, tr. 113.

Mục tiêu số → **hồi quy**; cần chính xác → có tham số hoặc phi tham số. Ứng viên: KNN, hồi quy tuyến tính, rừng ngẫu nhiên, gradient boosting. Dữ liệu **lớn, phức tạp** → chọn mô hình phức tạp tương ứng: **rừng ngẫu nhiên**.

**Rừng ngẫu nhiên (Random Forest)**: xây **nhiều cây quyết định độc lập**, **lấy trung bình** dự đoán. Chia train/test.

Ba chỉ số sai số hồi quy trên tập test (công thức là Mở rộng):

[![C1 Bốn ca học máy trong lecture – bảng 3](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.svg)](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.md)

> **note** Bảng dạng chữ
> | Chỉ số | Công thức | Đọc |
> | --- | --- | --- |
> | MAE (Mean Absolute Error) | $\frac{1}{n}\sum \lvert y_i - \hat y_i\rvert$ | Sai trung bình, **cùng đơn vị** với $y$ |
> | MSE (Mean Square Error) | $\frac{1}{n}\sum (y_i - \hat y_i)^2$ | Phạt nặng sai lớn, đơn vị **bình phương** |
> | R² (R-squared) | $1 - \frac{\sum (y_i-\hat y_i)^2}{\sum (y_i-\bar y)^2}$ | Tỷ lệ biến thiên được giải thích; càng gần 1 càng tốt |

### Kết quả

Nguồn tr. 114, tr. 115.

Slide in 10 dòng *Giá/m2_thực_tế* và *Giá/m2_dự_đoán* (ví dụ Đống Đa 270 → 200,45; Hà Đông 125 → 129,89). Kết luận: sai trung bình **khoảng 27–28 triệu/m²**; RF giải thích **khoảng 47%** biến thiên giá. Biểu đồ *So sánh giá thực tế và dự đoán* ghi **MAE = 27,88**, **hệ số xác định 0,461**. Các điểm nằm **dưới đường chéo** ở vùng giá cao → mô hình **đoán thấp** nhà đắt.

> **example** Tính lại trên 10 dòng slide in ra (đã chạy)
> ```python
> import numpy as np
> from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
> thuc = np.array([270, 125, 127.59, 79.03, 162.86, 78.57, 98.33, 100, 100, 120])
> du   = np.array([200.45, 129.89, 112.58, 74.64, 116.00, 76.31, 79.78, 133.04, 85.70, 117.05])
> print("MAE =", round(mean_absolute_error(thuc, du), 2))
> print("MSE =", round(mean_squared_error(thuc, du), 2))
> print("R2  =", round(r2_score(thuc, du), 3))
> ```
> ```text
> MAE = 21.18
> MSE = 895.56
> R2  = 0.688
> ```
> Mười dòng này chỉ là mẫu; MAE toàn tập test là 27,88. Không suy kết luận toàn tập từ 10 dòng.

> **warning** Dễ nhầm
> - R² ≈ 0,47 **không** có nghĩa "đúng 47% số căn". Nó là tỷ lệ **biến thiên** của giá được mô hình giải thích.
> - Slide chữ ghi "khoảng 47%", biểu đồ ghi 0,461: cùng một kết quả làm tròn.
> - Accuracy dùng cho phân loại; MAE/MSE/R² dùng cho **hồi quy**.

> **question** Tự kiểm tra: Hai căn giá thật 60 và 100, dự báo 50 và 120. Tính MAE, MSE, R².
> MAE $=(10+20)/2=15$. MSE $=(100+400)/2=250$. $\bar y=80$, $\sum(y-\bar y)^2 = 800$ → $R^2 = 1 - 500/800 = 0{,}375$.

## 4. Tìm khách hàng tiềm năng cho chiến dịch

### Bài toán và dữ liệu

Nguồn tr. 116–tr. 118.

Ngân hàng gọi điện mời **gửi tiết kiệm có kỳ hạn**. Ngân sách chỉ gọi được **2.000** trong **20.000** khách. Mục tiêu: chọn 2.000 người **có khả năng đồng ý cao nhất** để tối ưu **tỷ lệ chuyển đổi**.

[![C1 Bốn ca học máy trong lecture – bảng 4](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.svg)](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%20B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.md)

> **note** Bảng dạng chữ
> | Nhóm biến | Biến |
> | --- | --- |
> | Định danh | `ID` |
> | Nhân khẩu | `age`, `job` (admin, blue-collar, student, retired…), `marital` (single, married, divorced), `education` (primary, secondary, tertiary, unknown) |
> | Tài chính | *`default`* (nợ xấu), `balance` (số dư), `housing` (vay mua nhà), `loan` (vay cá nhân) |
> | Liên hệ hiện tại | `day`, `month`, `duration` (giây cuộc gọi cuối), `campaign` (số lần liên hệ chiến dịch này) |
> | Lịch sử | `pdays` (ngày từ lần liên hệ trước; 999 nếu chưa từng), `previous` (số lần liên hệ chiến dịch trước) |
> | **Mục tiêu** | `term_deposit` (yes/no) |

> **info** Mở rộng: cẩn thận với `duration`
> Thời lượng cuộc gọi chỉ biết **sau khi gọi**. Muốn chọn ai để gọi thì chưa có biến này. Dùng nó làm đầu vào là rò rỉ thông tin tương lai.

### Phân tích bài toán

Nguồn tr. 119–tr. 121.

- **Phân loại nhị phân có giám sát**: `term_deposit` = 0 (không) / 1 (đồng ý).
- Biến giải thích: thông tin khách (tuổi, nghề, tài sản…) và lịch sử tương tác.
- **Mất cân bằng**: chỉ khoảng **9,3%** đồng ý. Chọn ngẫu nhiên 2.000 → khoảng 180–186 người đồng ý.
- Trực quan: khách **có vay mua nhà** ít đồng ý hơn (92,2% không gửi so với 87,3%); khách **có khoản vay khác** cũng ít đồng ý (94,0% so với 90,1%).
- Theo nghề: **sinh viên 21,2%** và **nghỉ hưu 17,1%** đồng ý cao nhất; **blue-collar 6,4%** thấp nhất.

### Mô hình và kết quả

Nguồn tr. 122, tr. 123.

- Nhị phân → phân loại. Cần chính xác **nhưng phải giải thích** → **có tham số**. Ứng viên: logistic, cây quyết định, RF, gradient boosting. Chọn **hồi quy logistic** kết hợp mô hình khác để đối chiếu.
- **Hồi quy logistic** mở rộng hồi quy tuyến tính khi mục tiêu là lớp; cho ra **xác suất** đồng ý.
- So sánh: **ngẫu nhiên** 2.000 → ~9,3% → **186** người. **Theo mô hình**: xếp theo xác suất, lấy top 2.000 → **484** người.

$$\frac{484}{2000} = 24{,}2\%, \qquad \frac{484}{186} \approx 2{,}6 \text{ lần}$$

> **warning** Chênh số trên slide
> Ô code trên tr. 123 in **"Tỷ lệ chuyển đổi: 24.2%"**, đúng với $484/2000$. Dòng kết luận màu đỏ ghi "**24,7%**" là lỗi gõ. Trang 119 ghi "khoảng 180", trang 123 ghi "186" ($0{,}093 \times 2000 = 186$). Khi thi, tính lại từ tử và mẫu đề cho.

> **info** Mở rộng: logistic
> $P(y=1 \mid X) = \dfrac{1}{1+e^{-(\beta_0 + \beta_1 x_1 + \dots)}}$. Đầu ra trong khoảng (0, 1) nên dùng để **xếp hạng** khách.

> **question** Tự kiểm tra: Bốn khách có xác suất 0,80; 0,55; 0,20; 0,10. Chỉ gọi được 2. Chọn ai? Nếu 1 trong 2 đồng ý, tỷ lệ chuyển đổi là bao nhiêu?
> Chọn 0,80 và 0,55. Tỷ lệ $1/2 = 50\%$.

## Chốt lại

Quảng cáo và giá nhà dự báo **số** (hồi quy). Iris dự đoán **một trong ba lớp**. Chiến dịch có nhãn **nhị phân**, dùng xác suất để **xếp hạng**. Với mọi ca, ghi rõ đơn vị quan sát, biến biết trước, mục tiêu, cách giữ tập kiểm tra và điều kiện quyết định.

Áp dụng ở F106 Nhãn và loại bài toán, F103 Cấp độ phân tích. Nối sang [chương 8](../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md).
