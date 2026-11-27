# DataFrame: tạo, truy xuất và cập nhật

> **abstract** Tóm tắt
> **DataFrame** là bảng 2 chiều: nhãn hàng (*`index`*), nhãn cột (*`columns`*), mỗi cột là một Series có kiểu riêng. Tạo phổ biến nhất từ **dict các list cùng độ dài**. Chọn hàng bằng `iloc` (vị trí), *`loc`* (nhãn), điều kiện, hoặc duyệt **`iterrows`**. Chọn cột bằng `df["col"]` (Series) hay `df"c1","c2"` (DataFrame). Gán **list/ndarray** theo thứ tự và phải đúng độ dài; gán **Series** thì căn theo index, thiếu thành `NaN`.

Dữ liệu mẫu xuyên suốt (slide tr. 115):

```python
import pandas as pd, numpy as np
data = {"Tên": ["An", "Bình", "Cường"], "Tuổi": [20, 21, 19], "Điểm": [8.5, 7.0, 9.0]}
df = pd.DataFrame(data)
print(df)
#      Tên  Tuổi  Điểm
# 0     An    20   8.5
# 1   Bình    21   7.0
# 2  Cường    19   9.0
```

## Hàm tạo DataFrame và các tham số

Nguồn tr. 111.

**`pandas.DataFrame(data, index, columns, dtype, copy)`**

[![C3 11 DataFrame tạo, truy xuất và cập nhật – bảng 1](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Tham số | Ý nghĩa |
> | --- | --- |
> | *`data`* | ndarray, Series, list, dict, hằng số, hoặc DataFrame khác |
> | *`index`* | Nhãn hàng |
> | *`columns`* | Nhãn cột |
> | *`dtype`* | Kiểu dữ liệu cho mỗi cột |
> | *`copy`* | `True/False`: có chép sang vùng nhớ mới không, mặc định `False` |

> **warning** Slide gõ nhầm
> Tiêu đề slide ghi **`np.DataFrame()`**. Đúng là **`pd.DataFrame()`**; NumPy không có DataFrame.

## Tạo từ dict, list, mảng NumPy

Nguồn tr. 112, tr. 113, tr. 114, tr. 115.

Ba cách ở tr. 112–113 cho **cùng một bảng**:

```python
a1 = {'x': [1, 2, 3], 'y': np.array([2, 4, 8]), 'z': 100}     # dict: khóa = tên cột, 100 lặp
a2 = [{'x': 1, 'y': 2, 'z': 100}, {'x': 2, 'y': 4, 'z': 100},
      {'x': 3, 'y': 8, 'z': 100}]                              # list các dict: mỗi dict = 1 hàng
a3 = [[1, 2, 100], [2, 4, 100], [3, 8, 100]]                   # list lồng / ndarray 2D: cần columns
d3 = pd.DataFrame(a3, columns=['x', 'y', 'z'])
#    x  y    z
# 0  1  2  100
# 1  2  4  100
# 2  3  8  100
```

Đặt tên hàng bằng tham số *`index`* (tr. 114):

```python
dict1 = {"calories": [420, 380, 390], "duration": [50, 40, 45]}
print(pd.DataFrame(dict1, index=["day1", "day2", "day3"]))
#       calories  duration
# day1       420        50
# day2       380        40
# day3       390        45
```

## Tham số columns và dict lồng nhau

Nguồn tr. 116, tr. 117, tr. 118.

*`columns`* **sắp lại** thứ tự cột. Cột không có trong dict được tạo, toàn `NaN`:

```python
print(pd.DataFrame(data, columns=["Tên", "Điểm", "Tuổi"]))
#      Tên  Điểm  Tuổi
# 0     An   8.5    20 ...
print(pd.DataFrame(data, columns=["Tên", "Điểm", "Tuổi", "Địa chỉ"]))
#      Tên  Điểm  Tuổi Địa chỉ
# 0     An   8.5    20     NaN
# 1   Bình   7.0    21     NaN
# 2  Cường   9.0    19     NaN
```

**Dict lồng nhau**: khóa ngoài = **tên cột**, khóa trong = **chỉ số hàng**.

```python
data2 = {"Toán": {0: 8.5, 1: 7.0, 2: 9.0},
         "Văn":  {0: 6.5, 1: 8.0, 2: 7.5},
         "Anh":  {0: 9.0, 1: 6.5, 2: 8.0}}
print(pd.DataFrame(data2))
#    Toán  Văn  Anh
# 0   8.5  6.5  9.0
# 1   7.0  8.0  6.5
# 2   9.0  7.5  8.0
```

## Bảng đầu vào hợp lệ

Nguồn tr. 119.

[![C3 11 DataFrame tạo, truy xuất và cập nhật – bảng 2](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.svg)](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.md)

> **note** Bảng dạng chữ
> | Loại *`data`* | Ghi chú |
> | --- | --- |
> | dict của mảng 1D, list, dict hoặc Series | Mọi mảng phải **cùng độ dài**; nếu truyền index, độ dài index khớp độ dài mảng |
> | ndarray 2D | Xử lý như ma trận, thành DataFrame có nhãn hàng, cột |
> | ndarray có cấu trúc / bản ghi | Xử lý như dict của các Series |
> | Một Series | Index của Series thành index hàng |
> | Một DataFrame khác | Giữ index cũ, trừ khi truyền index khác |

## head và tail

Nguồn tr. 120.

Mặc định 5 hàng đầu / 5 hàng cuối.

```python
print(df.head(2))   # hàng 0 (An), 1 (Bình)
print(df.tail(2))   # hàng 1 (Bình), 2 (Cường)
```

> **warning** Slide chú thích sai
> Slide ghi `df.tail(2)  # 1 hàng cuối`. Thực tế là **2** hàng cuối.

## Truy xuất hàng

Nguồn tr. 121, tr. 122, tr. 123, tr. 124, tr. 125.

Bốn cách: **`.iloc[]`** theo vị trí, **`.loc[]`** theo nhãn, boolean indexing, duyệt **`.iterrows()`**.

```python
print(df.iloc[0])        # 1 hàng -> Series, nhãn là tên cột
# Tên      An
# Tuổi     20
# Điểm    8.5
# Name: 0, dtype: object
print(df.iloc0, 2)   # nhiều hàng -> DataFrame (An, Cường)

print(df.loc[1])         # hàng có NHÃN 1 (Bình)
print(df.loc2, 0)    # Cường rồi An, theo thứ tự đưa vào

df.index = ["sv1", "sv2", "sv3"]      # đặt lại index
print(df.loc["sv2"])                  # Bình
print(df.loc"sv1", "sv3")         # An, Cường

print(df[df["Điểm"] > 8])             # sv1 An 8.5, sv3 Cường 9.0
print(df[df["Tên"] == "Bình"])        # sv2 Bình

for index, row in df.iterrows():      # mỗi vòng: (nhãn, Series của hàng)
    print(index, row["Tên"], row["Điểm"])
# sv1 An 8.5
# sv2 Bình 7.0
# sv3 Cường 9.0
```

> **warning** Dễ nhầm
> Sau `df.index = ["sv1", ...]`, `df.loc[1]` báo **KeyError** vì nhãn 1 không còn. `df.iloc[1]` vẫn chạy vì vị trí không đổi.

## Truy xuất cột

Nguồn tr. 126, tr. 127, tr. 128, tr. 129, tr. 130, tr. 131.

```python
print(df["Tên"])                # Series (cách dict)
print(df.Tuổi)                  # Series (cách thuộc tính)
print(df"Tên", "Điểm")      # DataFrame 2 cột
print(df.iloc[:, 0].tolist())   # ['An', 'Bình', 'Cường']   cột vị trí 0
print(df.iloc[:, [0, 2]])       # cột Tên, Điểm
print(df.loc[:, "Tuổi"].tolist())   # [20, 21, 19]
print(df.loc[:, ["Tên", "Tuổi"]])
print(df.loc[df["Điểm"] > 8, "Tên"])   # sv1 An, sv3 Cường   lọc hàng + chọn cột
```

| Viết | Lấy | Kiểu kết quả |
| --- | --- | --- |
| `df["col"]` hoặc **`df.col`** | 1 cột | Series |
| `df"c1", "c2"` | nhiều cột | DataFrame |
| `df.iloc[:, idx]` | cột theo số thứ tự | Series (1 số) / DataFrame (list) |
| `df.loc[:, "col"]` | cột theo nhãn | Series / DataFrame |
| `df.loc[điều_kiện, "col"]` | lọc theo giá trị | Series |

[![Chọn loc hay iloc](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/Ch%E1%BB%8Dn%20loc%20hay%20iloc.excalidraw.svg)](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/Ch%E1%BB%8Dn%20loc%20hay%20iloc.excalidraw.md)

> **warning** Dễ nhầm
> `df["Tên"]` (một ngoặc) → Series. `df"Tên"` (hai ngoặc) → DataFrame một cột. **`df.Tuổi`** chỉ dùng được khi tên cột là định danh hợp lệ (không dấu cách, không trùng phương thức như **`count`**).

## Cập nhật giá trị

Nguồn tr. 132, tr. 133, tr. 134, tr. 135, tr. 136.

Theo dõi trạng thái bảng qua từng lệnh (slide chạy nối tiếp):

```python
df = pd.DataFrame(data)
df.iloc[0, 1] = 22                       # vị trí hàng 0, cột 1 (Tuổi của An)
df.loc[1, "Tuổi"] = 25                   # nhãn hàng 1, cột Tuổi
df.loc[2, ["Tuổi", "Điểm"]] = [20, 9.5]  # nhiều cột trên một hàng
print(df)
#      Tên  Tuổi  Điểm
# 0     An    22   8.5
# 1   Bình    25   7.0
# 2  Cường    20   9.5
df.loc[df["Điểm"] <= 8.5, "Điểm"] += 1   # cộng 1 cho ai có điểm <= 8.5
print(df)
#      Tên  Tuổi  Điểm
# 0     An    22   9.5
# 1   Bình    25   8.0
# 2  Cường    20   9.5     (9.5 > 8.5 nên giữ nguyên)
```

Cập nhật cả cột, và cập nhật nhanh một ô bằng `at` (nhãn) / `iat` (vị trí):

```python
df = pd.DataFrame(data)
df["Tuổi"] = df["Tuổi"] + 1    # 21, 22, 20
df.at[0, "Tên"] = "Anh"        # nhãn hàng 0, cột "Tên"
df.iat[1, 2] = 8.0             # vị trí hàng 1, cột 2 (Điểm của Bình)
print(df)
#      Tên  Tuổi  Điểm
# 0    Anh    21   8.5
# 1   Bình    22   8.0
# 2  Cường    20   9.0
```

[![C3 11 DataFrame tạo, truy xuất và cập nhật – bảng 3](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.svg)](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.md)

> **note** Bảng dạng chữ
> | Công cụ | Chọn bằng | Phạm vi |
> | --- | --- | --- |
> | `iloc` | vị trí | ô, hàng, cột, khối |
> | *`loc`* | nhãn / điều kiện | ô, hàng, cột, khối |
> | `at` | nhãn | **đúng một ô**, nhanh |
> | `iat` | vị trí | **đúng một ô**, nhanh |

## Gán cột bằng list, ndarray hay Series

Nguồn tr. 137, tr. 138, tr. 139.

[![C3 11 DataFrame tạo, truy xuất và cập nhật – bảng 4](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.svg)](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2011%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.md)

> **note** Bảng dạng chữ
> | Loại dữ liệu gán | Yêu cầu | Đặc điểm |
> | --- | --- | --- |
> | list hoặc ndarray | Độ dài **=** số hàng | Gán tuần tự theo thứ tự hàng |
> | Series | Không bắt buộc bằng số hàng | **Căn theo index**, nhãn thiếu → `NaN` |

```python
df = pd.DataFrame({"Tên": ["An", "Bình", "Cường"], "Tuổi": [20, 21, 19]})
df["Điểm"] = [8.5, 7.0, 9.0]                         # list đủ 3
df["Xếp loại"] = np.array(["Khá", "TB", "Giỏi"])     # ndarray đủ 3
df["X"] = [1, 2]
# ValueError: Length of values (2) does not match length of index (3)

diem_series = pd.Series(data=[10, 9], index=[0, 2], name="Điểm mới")
df["Điểm mới"] = diem_series
print(df)
#      Tên  Tuổi  Điểm Xếp loại  Điểm mới
# 0     An    20   8.5      Khá      10.0
# 1   Bình    21   7.0       TB       NaN
# 2  Cường    19   9.0     Giỏi       9.0
```

Đây là cơ chế mạnh: chỉ cần index khớp, không cần quan tâm thứ tự hàng.

> **warning** Dễ nhầm
> Cột "Điểm mới" thành **float64** (10.0, 9.0) vì có NaN. Series có 2 phần tử vẫn gán được vào bảng 3 hàng, còn list 2 phần tử thì lỗi.

> **question** Tự kiểm tra
> 1. **`pd.DataFrame({"a": [1, 2]}, columns=["a", "b"])`** cột b chứa gì? → `NaN, NaN`.
> 2. Dict lồng `{"X": {0: 1, 1: 2}}`: khóa `"X"` thành gì? → tên cột.
> 3. `df.iloc[0]` trả kiểu gì? → Series.
> 4. Bảng index `[10, 20, 30]`. `df.loc[20]` và `df.iloc[1]` có cùng hàng không? → Có, cùng hàng thứ hai.
> 5. `df.loc[df["Điểm"] > 8, "Tên"]` trả kiểu gì? → Series tên các bạn điểm > 8.
> 6. Gán `df["c"] = pd.Series([5], index=[1])` cho bảng 3 hàng (index 0,1,2)? → `[NaN, 5.0, NaN]`.
> 7. Cách nhanh nhất sửa một ô theo nhãn? → `df.at[nhãn_hàng, "cột"]`.

Áp dụng ở F309 Tạo DataFrame và đọc cấu trúc bảng, F310 Chọn dòng-cột bằng loc, iloc và điều kiện, F312 Hàm tóm tắt, sắp xếp và apply trong Pandas. Học tiếp [04 Index và căn chỉnh Pandas](04%20Index%20v%C3%A0%20c%C4%83n%20ch%E1%BB%89nh%20Pandas.md).
