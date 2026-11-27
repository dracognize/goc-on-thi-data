# Thực hành thêm · Ghép theo index và tổng hợp doanh số

## Ghép bằng cột bên trái với index bên phải

Đơn hàng có thể lặp mã khách. Bảng danh mục khách có một hàng trên mỗi mã. Cả hai kiểu ghép dưới đây dùng cùng khóa. Khóa phía phải chuyển từ cột thành index trong cách thứ hai. Lec 6 · Ghép dựa trên index

```python
import pandas as pd

orders = pd.DataFrame({"ma": ["A", "A", "B", "C"], "so_luong": [1, 2, 1, 3]})
customers = pd.DataFrame({"ma": ["A", "B"], "vung": ["Bắc", "Nam"]})
by_column = orders.merge(customers, on="ma", how="left", validate="many_to_one")
customer_lookup = customers.set_index("ma", verify_integrity=True)
by_index = orders.merge(
    customer_lookup, left_on="ma", right_index=True,
    how="left", validate="many_to_one",
)

pd.testing.assert_frame_equal(by_column.reset_index(drop=True), by_index.reset_index(drop=True))
assert len(by_index) == len(orders)
assert by_index["vung"].isna().tolist() == [False, False, False, True]
```

- **Trước ghép:** Bảng đơn có hai dòng mã A. Danh mục chỉ có một dòng A. `many_to_one` kiểm tra cấu trúc nhiều–một.
- **Sau ghép:** A nhận vùng Bắc hai lần, B nhận vùng Nam, C giữ lại theo left join và thiếu vùng. Tổng số lượng vẫn bằng 7.
- **Nếu cần kiểm định hiệu năng:** Kiểm tra hai cách cho cùng dữ liệu trước khi đo. Đo vài lượt cho mỗi cách với cùng thao tác ghép. Tách thời gian tạo index nếu index đã được dùng lại, rồi đo phép ghép kèm tạo index nếu chỉ thực hiện một lần.

Có thể chạy tiếp sau khối trên. Kết quả phụ thuộc máy và kích thước dữ liệu. Mẫu nhỏ giúp hiểu cách đo.

```python
from statistics import median
from timeit import repeat

def merge_column():
    return orders.merge(customers, on="ma", how="left", validate="many_to_one")

def merge_reused_index():
    return orders.merge(customer_lookup, left_on="ma", right_index=True,
                        how="left", validate="many_to_one")

def merge_new_index():
    lookup = customers.set_index("ma", verify_integrity=True)
    return orders.merge(lookup, left_on="ma", right_index=True,
                        how="left", validate="many_to_one")

for operation in [merge_column, merge_reused_index, merge_new_index]:
    samples = repeat(operation, repeat=5, number=100)
    print(operation.__name__, round(median(samples) / 100 * 1000, 3), "ms/lần")
```

Lec 6 · Đối chiếu tốc độ

## Ghép nhiều chi nhánh và đọc câu hỏi đúng đơn vị

Lưu nhãn chi nhánh trước khi ghép. Với dữ liệu xếp dọc, mỗi dòng vẫn là một bản ghi bán hàng. Sau đó mới tính thành tiền và tổng hợp.

```python
import pandas as pd

hn = pd.DataFrame({"sp": ["Laptop", "Chuột"], "luong": [2, 5], "gia": [12, 1]})
dn = pd.DataFrame({"sp": ["Laptop", "Chuột"], "luong": [1, 4], "gia": [13, 1]})
sales = pd.concat([hn.assign(cn="Hà Nội"), dn.assign(cn="Đà Nẵng")], ignore_index=True)
sales["tien"] = sales["luong"] * sales["gia"]

ledger = sales.set_index(["cn", "sp"])
summary = ledger.groupby(level="sp")"luong", "tien".sum()
assert summary.loc["Chuột"].tolist() == [9, 9]
assert summary.loc["Laptop"].tolist() == [3, 37]
assert ledger["tien"].sum() == 46
```

1. **`assign(cn=...)`** thêm cột nguồn vào từng bảng. **`concat`** xếp dọc, tạo bốn hàng.
2. `luong * gia` tính thành tiền mỗi dòng. Đơn vị ví dụ là triệu đồng.
3. **`groupby(level="sp")`** gom qua các chi nhánh theo tên sản phẩm. Chuột bán nhiều đơn vị nhất, Laptop có doanh thu cao hơn.
4. Lấy doanh thu từng sản phẩm chia doanh thu toàn hệ thống. Tỷ trọng Laptop là $37/46$, khoảng 80,4%. Nếu câu hỏi chuyển sang tỷ trọng *trong mỗi chi nhánh*, mẫu số phải là tổng của từng chi nhánh.

> **question** Khi ước lượng tổng doanh số sau merge cần kiểm tra gì?
> Đếm dòng theo khóa trước và sau. Khóa trùng cả hai phía có thể nhân số dòng. Tính lại tổng và so với mức dự kiến trước khi báo cáo.

Lec 6 · Tham số concat · Bài toán tổng hợp đại lý · Về mục lục Lec 6
