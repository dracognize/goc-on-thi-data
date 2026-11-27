# Đổi wide long và tổng hợp ô trùng

**Lý thuyết.** [Melt pivot stack và unstack](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/04%20Melt%20pivot%20stack%20v%C3%A0%20unstack.md) · [Bảng tra chương 6](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Xác định cột định danh, biến đo, nhãn mới và giá trị. Trước khi pivot, kiểm tra tính duy nhất của cặp khóa hàng–cột.

## Ví dụ có lời giải

Ví dụ mới: hàng A có cột T1=12, T2=18. `melt` đổi thành `(A,T1,12)` và `(A,T2,18)`. Nếu thêm dòng `(A,T1,3)`, dùng `pivot_table(..., aggfunc='sum')` khi cần cộng để được T1=15.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Trong hàm melt, hai tham số var_name và value_name khác nhau như thế nào?

- **A.** var_name đặt tên cột chứa giá trị của các ô; value_name đặt tên cột chứa tên các cột đã gộp
- **B.** var_name đặt tên cột chứa tên các cột cũ đã gộp; value_name đặt tên cột chứa giá trị của các ô
- **C.** var_name đặt tên cho chỉ mục dòng của bảng mới; value_name đặt tên cho chỉ mục cột của bảng mới
- **D.** var_name chọn các cột được giữ nguyên làm định danh; value_name chọn các cột cần gộp lại

> **tip** Gợi ý
> Ở đầu ra, một cột chứa tên cột cũ và một cột chứa dữ liệu.

> **success** Đáp án B
> `var_name` đặt tên cột chứa nhãn cột cũ. `value_name` đặt tên cột chứa giá trị các ô.

Nguồn ScoreUp, nhóm 6, ID `Q02476`.

### 2 · Vận dụng

Đoạn code sau in ra dòng nào (chỉ số iloc = 2) của df_long?

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'SanPham': ['A', 'B'],
    'Q1': [100, 200],
    'Q2': [150, 250]
})
df_long = df.melt(id_vars=['SanPham'], value_vars=['Q1', 'Q2'], var_name='Quy', value_name='DoanhSo')
print(df_long.iloc[2])
```

- **A.** SanPham='B', Quy='Q1', DoanhSo=200
- **B.** SanPham='A', Quy='Q1', DoanhSo=100
- **C.** SanPham='A', Quy='Q2', DoanhSo=150
- **D.** SanPham='B', Quy='Q2', DoanhSo=250

> **tip** Gợi ý
> Viết thứ tự các dòng theo `value_vars`: Q1 rồi Q2.

> **success** Đáp án C
> Các dòng theo thứ tự A–Q1, B–Q1, A–Q2, B–Q2. `iloc[2]` là A–Q2 với doanh số 150.

Nguồn ScoreUp, nhóm 6, ID `Q02478`.

### 3 · Tổng hợp

Giả sử trong dữ liệu chấm công dạng long, nhân viên 'An' có hai bản ghi cùng ngày '2025-08-01' (do chấm công 2 lần trong ngày), sau đó ta gọi df_long.pivot(index='Employee', columns='Date', values='Hours'). Điều gì sẽ xảy ra?

- **A.** pivot() báo lỗi ValueError vì có hai giá trị cho cùng cặp (Employee, Date) và không tự gộp được.
- **B.** pivot() sẽ tự động cộng dồn hai giá trị Hours của hai lần chấm công thành một ô duy nhất.
- **C.** pivot() sẽ giữ lại giá trị Hours của bản ghi xuất hiện đầu tiên và âm thầm bỏ qua bản ghi còn lại.
- **D.** pivot() sẽ tạo ra hai cột riêng biệt cùng tên ngày '2025-08-01' để chứa cả hai giá trị.

> **tip** Gợi ý
> Mỗi ô kết quả có thể chứa bao nhiêu giá trị trước khi tổng hợp?

> **success** Đáp án A
> Hai bản ghi An cùng ngày ánh xạ vào một ô. `pivot` báo `ValueError`. Dùng `pivot_table` nếu đã quyết định tổng hợp.

Nguồn ScoreUp, nhóm 6, ID `Q02530`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
