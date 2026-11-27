# Tự kiểm tra · Chương 5

Đóng slide, viết đáp án và lý do trước khi mở từng thẻ. Ghi lại câu sai hoặc đoán để ôn sau 1, 3 và 7 ngày. Ôn thêm bằng Thẻ nhớ chương 5.

## Khởi động

> **question** Bắt đầu. Cột điểm có 8, 0, None. Có mấy ô thiếu? Vì sao?
> Một. None biểu thị chưa có dữ liệu. 0 có thể là điểm thật nếu nguồn không quy ước 0 là ký hiệu thiếu.

> **question** 1. Hai dòng có cùng tên khách hàng, có nên xóa một dòng?
> Kiểm tra đơn vị quan sát và khóa nghiệp vụ. Trùng tên không chứng minh hai dòng là cùng bản ghi.

## Dữ liệu thiếu (5.1)

> **question** 2. Khách trẻ tuổi hay bỏ trống thu nhập. MCAR, MAR hay MNAR?
> **MAR**: xác suất thiếu phụ thuộc biến khác (tuổi), không phụ thuộc trực tiếp thu nhập.

> **question** 3. Pandas biểu diễn thiếu cho số, object, thời gian bằng gì?
> `NaN`, `None`, `NaT`.

> **question** 4. `df_missing` (Tuổi thiếu 2, Lương thiếu 1, Phòng ban thiếu 1). `isna().sum().sum()`?
> 4.

> **question** 5. `df_missing.dropna()`, `dropna(how='all')`, `dropna(axis=1)` còn bao nhiêu?
> 2 hàng · 5 hàng · 1 cột (Tên).

> **question** 6. Tuổi [25, NaN, 30, 28, NaN]. Điền mean và median được bao nhiêu?
> Mean 27,67 · median 28.

> **question** 7. Cột Phòng ban có IT ×2, Marketing ×2. `mode()[0]` là gì?
> `IT`. Khi hòa, **`mode()`** trả cả hai theo thứ tự sắp xếp, `[0]` lấy giá trị đầu.

> **question** 8. `[NaN, 5, NaN, 9]` sau ffill và bfill?
> ffill `[NaN, 5, 5, 9]` · bfill `[5, 5, 9, 9]`.

> **question** 9. Dữ liệu số thiếu 12% và các biến tương quan mạnh. Slide khuyên gì?
> KNN hoặc Random Forest (5–20% thiếu + có correlation).

> **question** 10. Vì sao LabelEncoder cần `fillna('Unknown')` trước?
> LabelEncoder không xử lý được NaN.

> **question** 11. Trong `for i, (idx, row) in enumerate(missing_data.iterrows())`, vì sao dùng `predicted[i]` chứ không phải `predicted[idx]`?
> `predicted` là mảng NumPy đánh số 0, 1, 2. `idx` là nhãn index (1, 4, 6), dùng sẽ sai hoặc lỗi.

> **question** 12. KNNImputer `n_neighbors=2`, láng giềng có Tuổi 30 và 32. Ô được điền?
> 31.

## Dữ liệu trùng (5.2)

> **question** 13. `['A','B','A','A'].duplicated()` với keep mặc định?
> `[False, False, True, True]`.

> **question** 14. Mã khách A có hai bản ghi đúng thứ tự cũ đến mới. `duplicated(keep='last')` đánh dấu bản nào?
> Bản cũ. True nghĩa là bản bị xem là lặp theo quy tắc giữ bản cuối.

> **question** 15. Tham số nào của `drop_duplicates` đánh lại index?
> *`ignore_index=True`*.

## Scale (5.3)

> **question** 16. Có ba giá trị 10, 15, 30. Min-max của 15?
> $(15-10)/(30-10)=0.25$.

> **question** 17. Sau khi fit min-max trên [10, 20, 30], vì sao test 35 cho 1,25?
> Dùng min, max đã học từ train: $(35-10)/20=1.25$. Không ép về [0, 1].

> **question** 18. Sau StandardScaler, `df.std()` in 1,118 với 5 hàng. Lỗi?
> Không. Pandas std dùng mẫu số $n-1$, scaler dùng $n$: $\sqrt{5/4}=1{,}118$.

> **question** 19. Lương có một outlier 200 triệu. Scaler nào giữ lương bình thường trải đều quanh 0?
> RobustScaler (median, IQR).

> **question** 20. Vì sao fit scaler trên toàn bộ dữ liệu rồi mới tách là sai quy trình đánh giá?
> Tham số biến đổi chịu ảnh hưởng của test, gây rò rỉ thông tin.

## Chuỗi (5.4)

> **question** 21. `pd.Series(['Alber@t']).str.find('e')` và `.str.findall('e')`?
> `3` và `'e'`.

> **question** 22. `pd.Series(['Tom ']).str.endswith('m')`?
> False. Chuỗi kết thúc bằng dấu cách.

> **question** 23. Regex `\d+` trên `"Phòng 305"` cho gì?
> `305`.

> **question** 24. Hai nhãn " Hà Nội " và "hà nội" thành gì sau strip và lower?
> Cùng "hà nội", dùng chung một cờ one-hot.

## Phân loại (5.5)

> **question** 25. `pd.Categorical(['Khá','Giỏi','Kém'], categories=['Kém','Khá','Giỏi'], ordered=True).codes`?
> `[1, 2, 0]`.

> **question** 26. Thành phố và hạng dịch vụ nên mã hóa thế nào?
> Thành phố (nominal) one-hot. Hạng dịch vụ (ordinal) mã thứ tự có ánh xạ tường minh.

> **question** 27. 3 cột phân loại mỗi cột 3 giá trị + cột Tên. `get_dummies` và `OneHotEncoder(drop='first')` cho mấy cột?
> 10 cột và 7 cột (kể cả Tên).

> **question** 28. Ba nhược điểm của one-hot?
> Curse of dimensionality, sparse matrix, multicollinearity.

Sau lượt đầu, thay dữ kiện trong một câu và giải lại. Ôn quy tắc trong [05 Công thức và cú pháp](05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md).

Mục lục chương 5
