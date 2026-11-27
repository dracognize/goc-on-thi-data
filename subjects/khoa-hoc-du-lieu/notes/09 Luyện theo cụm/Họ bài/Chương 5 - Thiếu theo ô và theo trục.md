# Thiếu theo ô và theo trục

**Lý thuyết.** [Thiếu và trùng](../../05%20L%C3%A0m%20s%E1%BA%A1ch/01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) · [Bảng tra chương 5](../../05%20L%C3%A0m%20s%E1%BA%A1ch/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Xác định hướng thao tác trước khi tính. `isna` tạo mask theo ô, `dropna(subset=...)` xét chỉ các cột được nêu khi bỏ hàng. `ffill` và `bfill` cần nguồn ở phía tương ứng.

## Ví dụ có lời giải

Ví dụ mới: cột `score` là `[NaN, 2, NaN, 4, NaN]`. Điền tiến cho `[NaN, 2, 2, 4, 4]`. Điền lùi cho `[2, 2, 4, 4, NaN]`. Mỗi phía còn một ô thiếu ở biên khác nhau.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Hàm nào trả về True tại những vị trí có giá trị thiếu (NaN)?

- **A.** pd.notna()
- **B.** pd.dropna()
- **C.** pd.isnull() hoặc pd.isna()
- **D.** pd.fillna()

> **tip** Gợi ý
> Cần mask True ở ô thiếu.

> **success** Đáp án C
> `pd.isna` và `pd.isnull` tương đương với tác vụ này.

Nguồn ScoreUp, nhóm 5, ID `Q01920`.

### 2 · Vận dụng

Đoạn code sau dùng dropna(subset=['Luong']) để chỉ xét dữ liệu thiếu ở cột 'Luong'. Đoạn code in ra số hàng còn lại trong result3 là bao nhiêu?

```python
import pandas as pd
import numpy as np

data3 = {
    'Ten': ['An', 'Binh', 'Chi'],
    'Luong': [15000000, None, 20000000],
    'Thuong': [None, 2000000, 3000000]
}
df3 = pd.DataFrame(data3)
result3 = df3.dropna(subset=['Luong'])
print(len(result3))
```

- **A.** 2
- **B.** 3
- **C.** 1
- **D.** 0

> **tip** Gợi ý
> Liệt kê các hàng có Lương trống.

> **success** Đáp án A
> Bình thiếu Lương nên bị bỏ. An thiếu Thưởng vẫn được giữ vì `subset` chỉ gồm Lương. Còn hai hàng.

Nguồn ScoreUp, nhóm 5, ID `Q01915`.

### 3 · Tổng hợp

Bảng giá và khối lượng giao dịch của một mã cổ phiếu có ô thiếu ở đầu chuỗi và ở giữa chuỗi. Điền riêng bằng ffill() và bằng bfill() rồi đếm số ô còn thiếu, hai số in ra lần lượt là gì?

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'gia': [None, None, 100, None],
    'khoi_luong': [1000, None, 1500, 1800]
})
print(df.ffill().isna().sum().sum(), df.bfill().isna().sum().sum())
```

- **A.** 2 1
- **B.** 1 2
- **C.** 2 2
- **D.** 0 0

> **tip** Gợi ý
> Đếm ô không có nguồn điền ở mỗi đầu cột.

> **success** Đáp án A
> `ffill` còn hai ô đầu cột gia. `bfill` còn một ô cuối cột gia. Các ô thiếu giữa cột khoi_luong được điền theo cả hai hướng.

Nguồn ScoreUp, nhóm 5, ID `Q01988`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
