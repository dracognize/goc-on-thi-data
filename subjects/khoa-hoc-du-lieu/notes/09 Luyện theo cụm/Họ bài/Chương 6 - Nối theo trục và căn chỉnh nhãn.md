# Nối theo trục và căn chỉnh nhãn

**Lý thuyết.** [Merge concat và combine_first](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/03%20Merge%20concat%20v%C3%A0%20combine_first.md) · [Bảng tra chương 6](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Chọn trục xếp và chiều căn nhãn. Khi `axis=0`, `join` quyết định hợp hay giao cột, còn `ignore_index` tác động lên nhãn hàng.

## Ví dụ có lời giải

Ví dụ mới: hai bảng có số dòng 2 và 3, cột lần lượt `[id, sales]` và `[id, region]`. Nối hàng mặc định có shape `(5,3)` với các ô thiếu do lệch schema. Nối `join='inner'` còn đúng cột `id`, shape `(5,1)`.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Ba đại lý gửi ba bảng doanh thu, mỗi bảng có chỉ số hàng là 0 và 1. Khi nối chúng theo hàng bằng pd.concat, muốn bảng kết quả có chỉ số liên tục 0, 1, 2, 3, 4, 5 thì phải đặt đối số nào?

- **A.** ignore_index=True để bỏ chỉ số cũ và đánh lại chỉ số mới
- **B.** keys=['A', 'B', 'C'] để tạo chỉ số phân cấp và đánh số lại cấp trong
- **C.** verify_integrity=True để pandas tự sửa các chỉ số bị trùng lặp
- **D.** join='inner' để giữ lại các chỉ số không bị trùng giữa các bảng

> **tip** Gợi ý
> Giữ dữ liệu hàng, thay nhãn hàng bằng chỉ số mới.

> **success** Đáp án A
> `ignore_index=True` đánh lại chỉ số trên trục đang nối, 0 đến 5.

Nguồn ScoreUp, nhóm 6, ID `Q02475`.

### 2 · Vận dụng

Chạy đoạn code, hai số in ra là tổng số dòng của all_sales và số ô thiếu trong cột discount. Kết quả nào đúng?

```python
import pandas as pd

online = pd.DataFrame({
    'product': ['Laptop', 'Mouse', 'Tablet'],
    'amount': [1200, 20, 300]
})
store = pd.DataFrame({
    'product': ['Laptop', 'Phone'],
    'amount': [1250, 400],
    'discount': [50, 20]
})

all_sales = pd.concat([online, store])
print(len(all_sales), all_sales['discount'].isna().sum())
```

- **A.** 5 2
- **B.** 5 3
- **C.** 5 0
- **D.** 3 3

> **tip** Gợi ý
> Đếm tổng dòng rồi kiểm tra bảng nào không khai báo discount.

> **success** Đáp án B
> Có 3+2=5 dòng. Bảng online không có cột discount, nên ba hàng online có ô thiếu.

Nguồn ScoreUp, nhóm 6, ID `Q02490`.

### 3 · Tổng hợp

Đoạn mã đã cho nối hai bảng theo hàng, bảng thứ hai có thêm cột Type. Hai dòng in ra theo thứ tự là gì?

```python
import pandas as pd

a = pd.DataFrame({'Store': [1, 2], 'Sales': [100, 200]})
b = pd.DataFrame({'Store': [3, 4], 'Sales': [300, 400], 'Type': ['A', 'B']})
print(pd.concat([a, b]).shape)
print(pd.concat([a, b], join='inner').shape)
```

- **A.** (4, 2) rồi (4, 3)
- **B.** (4, 3) rồi (2, 3)
- **C.** (2, 3) rồi (2, 2)
- **D.** (4, 3) rồi (4, 2)

> **tip** Gợi ý
> Inner áp dụng lên nhãn của trục còn lại khi xếp theo hàng.

> **success** Đáp án D
> Mặc định dùng hợp ba cột nên được `(4, 3)`. Inner dùng giao hai cột Store và Sales nên được `(4, 2)`.

Nguồn ScoreUp, nhóm 6, ID `Q02497`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
