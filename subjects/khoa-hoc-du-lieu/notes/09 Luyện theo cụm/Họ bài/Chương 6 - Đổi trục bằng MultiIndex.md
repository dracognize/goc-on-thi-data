# Đổi trục bằng MultiIndex

**Lý thuyết.** [MultiIndex](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/01%20MultiIndex.md) · [Bảng tra chương 6](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Ghi thứ tự các cấp trước khi thao tác. `xs` chọn lát cắt theo cấp. `unstack` chuyển cấp đã chọn sang trục cột.

## Ví dụ có lời giải

Ví dụ mới: index `(Region, Quarter)` có North/South và Q1/Q2, các cặp đầy đủ. `unstack('Quarter')` giữ Region làm hàng và đưa Q1, Q2 xuống cấp trong của cột, cho bảng hai hàng hai cột nếu chỉ có một biến đo.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Trong pandas, "chỉ số phân cấp" (hierarchical indexing / MultiIndex) cho phép điều gì?

- **A.** Một trục của DataFrame có nhiều cấp chỉ mục lồng nhau, giúp biểu diễn dữ liệu nhiều chiều trong bảng 2 chiều
- **B.** Thay toàn bộ chỉ mục hiện có bằng dãy số thứ tự 0, 1, 2, ... mặc định để các dòng được đánh số lại
- **C.** Buộc mọi cột dữ liệu của DataFrame phải chuyển sang kiểu số nguyên để có thể dùng làm chỉ mục
- **D.** Giới hạn DataFrame ở tối đa hai cột, sao cho mỗi dòng được xác định bởi một cặp giá trị cột

> **tip** Gợi ý
> Nhãn trên một trục có thể là tuple.

> **success** Đáp án A
> Một trục có thể có nhiều cấp nhãn, như `(vùng, tháng)`.

Nguồn ScoreUp, nhóm 6, ID `Q02492`.

### 2 · Vận dụng

Bảng df1 có chỉ số bốn cấp (Region, Channel, Year, Quarter) và cột Revenue. Chỉ số hàng của kết quả df1.xs('Q1', level='Quarter') gồm những cấp nào?

- **A.** Quarter, vì cấp được chọn bằng level sẽ được giữ làm chỉ số
- **B.** Region, Channel và Year, cấp Quarter bị bỏ vì đã được chọn
- **C.** Region, Channel, Year và Quarter, bốn cấp đều được giữ lại
- **D.** Channel, Year và Quarter, cấp ngoài cùng Region bị bỏ đi

> **tip** Gợi ý
> Bỏ cấp đã chọn khi `xs` dùng cấu hình mặc định.

> **success** Đáp án B
> Chọn Q1 ở Quarter, với `drop_level=True` mặc định thì còn Region, Channel và Year.

Nguồn ScoreUp, nhóm 6, ID `Q02465`.

### 3 · Tổng hợp

Đoạn mã đã cho dùng unstack(level=0) trên bảng có chỉ số hàng (Region, Quarter). Hai dòng in ra theo thứ tự là gì?

```python
import pandas as pd

df = pd.DataFrame({
    'Region': ['North', 'North', 'South', 'South'],
    'Quarter': ['Q1', 'Q2', 'Q1', 'Q2'],
    'Revenue': [100, 130, 90, 95]
})
df1 = df.set_index(['Region', 'Quarter'])
rong = df1.unstack(level=0)
print(rong.loc['Q2', ('Revenue', 'South')])
print(rong.shape)
```

- **A.** 130 rồi (2, 2)
- **B.** Lỗi KeyError
- **C.** 90 rồi (2, 2)
- **D.** 95 rồi (2, 2)

> **tip** Gợi ý
> Level 0 là Region. Viết trục mới và tìm đúng giao điểm.

> **success** Đáp án D
> Hàng là Quarter, cột là cặp `(Revenue, Region)`. Q2 tại South là 95. Hai quý × hai vùng cho shape `(2, 2)`.

Nguồn ScoreUp, nhóm 6, ID `Q02505`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
