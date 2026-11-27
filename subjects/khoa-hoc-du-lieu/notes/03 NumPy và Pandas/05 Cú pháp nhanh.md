# Cú pháp nhanh · Chương 03

Cách đọc lời gọi **`np.arange(2, 8, 2)`**: `np` là tên ngắn thư viện, **`arange`** là hàm, ba đối số là mốc đầu 2, mốc ngoài 8 và bước 2. Kết quả là `[2, 4, 6]`. Một phương thức như **`a.reshape(...)`** nằm trên chính đối tượng `a`. Thuộc tính như `a.shape` lấy thông tin bằng tên, không thêm dấu gọi `()`.

[![C3 05 Cú pháp nhanh – bảng 1](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2005%20C%C3%BA%20ph%C3%A1p%20nhanh%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/03%20NumPy%20v%C3%A0%20Pandas/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C3%2005%20C%C3%BA%20ph%C3%A1p%20nhanh%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Thao tác | Cú pháp | Điểm cần kiểm tra |
> | --- | --- | --- |
> | Tạo mảng số | **`np.arange(start, stop, step)`** | Mốc cuối bị loại |
> | Đổi shape | **`a.reshape(2, -1)`** | Giữ size và chỉ một chiều suy ra |
> | Reduce | **`a.sum(axis=0)`** | Trục 0 bị gộp, còn một kết quả mỗi cột ở mảng 2D |
> | Theo điều kiện | **`np.where(mask, x, y)`** | Các shape cần broadcast được |
> | Nhân ma trận | `A @ B` | Hai kích thước trong bằng nhau với mảng 2D |
> | Cắt bảng theo vị trí | `df.iloc[0:3, 1:]` | Tối đa 3 hàng đầu, bắt đầu từ cột thứ hai |
> | Lọc và lấy cột | `df.loc[df["x"] > 0, ["x", "y"]]` | Giữ nhãn hàng |
> | Kiểm tra ô thiếu | **`df.isna().sum()`** | Đếm ô thiếu theo cột |
> | Căn theo nhãn | **`s.reindex(labels)`** | Nhãn không có dữ liệu tạo ô thiếu |

## API theo đầu vào và kết quả

| API | Ví dụ ngắn | Kết quả hoặc tác động |
| --- | --- | --- |
| **`np.array(values, dtype=...)`** | **`np.array([1,2], dtype=float)`** | Mảng chứa 1.0 và 2.0 |
| **`np.zeros(shape)`**, **`np.ones(shape)`** | **`np.ones((2,3))`** | Bảng 2 × 3 toàn số 1 |
| **`np.linspace(start, stop, num)`** | **`np.linspace(0, 1, 3)`** | `[0.0, 0.5, 1.0]`, mặc định gồm cả mốc cuối |
| **`a.astype(dtype)`** | **`np.array([1.9,2.1]).astype(int)`** | Mảng nguyên `[1,2]`, không làm tròn gần nhất |
| **`a.flatten()`** | **`np.array(1,2).flatten()`** | Bản sao một chiều `[1,2]` |
| **`df.head(n)`**, **`df.tail(n)`** | **`df.head(2)`** | Hai hàng đầu nếu đủ, vẫn là DataFrame |
| **`s.value_counts()`** | **`pd.Series(["A","A","B"]).value_counts()`** | A có 2, B có 1 |
| `idx.is_unique`, `idx.has_duplicates` | `pd.Index(["A","A"]).is_unique` | False. Dùng kiểm tra nhãn trước khi dựa vào tính duy nhất |
| **`idx.intersection(other)`** | **`pd.Index(["A","B"]).intersection(["B","C"])`** | Index chỉ chứa B |

## Bổ sung theo slide

| Thao tác | Cú pháp | Điểm cần kiểm tra | Note |
| --- | --- | --- | --- |
| Đổi thứ tự trục | **`np.transpose(a, (1, 0, 2))`**, **`np.swapaxes(a, 0, 2)`** | Shape mới = shape cũ tra theo axes | [tr. 37–39](01%20Shape%20axis%20v%C3%A0%20broadcasting.md) |
| Fancy indexing 2D | `a[[1, 2], [3, 0]]` | Ghép cặp (hàng, cột), ra 1D | [tr. 45–46](03%20Truy%20c%E1%BA%ADp%20v%C3%A0%20ph%C3%A9p%20to%C3%A1n%20NumPy.md) |
| Đếm True | `(a > 0).sum()` | True = 1 | [tr. 61](09%20Th%E1%BB%91ng%20k%C3%AA%2C%20t%E1%BA%ADp%20h%E1%BB%A3p%20v%C3%A0%20%C4%91%E1%BA%A1i%20s%E1%BB%91%20tuy%E1%BA%BFn%20t%C3%ADnh.md) |
| Tập hợp | **`np.unique`**, **`np.isin`**, **`np.intersect1d`** | Kết quả đã sắp | [tr. 63–65](09%20Th%E1%BB%91ng%20k%C3%AA%2C%20t%E1%BA%ADp%20h%E1%BB%A3p%20v%C3%A0%20%C4%91%E1%BA%A1i%20s%E1%BB%91%20tuy%E1%BA%BFn%20t%C3%ADnh.md) |
| Nhân ma trận | `x @ y`, **`x.dot(y)`**, **`np.linalg.inv`** | `(m,n) @ (n,p)` | [tr. 66–68](09%20Th%E1%BB%91ng%20k%C3%AA%2C%20t%E1%BA%ADp%20h%E1%BB%A3p%20v%C3%A0%20%C4%91%E1%BA%A1i%20s%E1%BB%91%20tuy%E1%BA%BFn%20t%C3%ADnh.md) |
| Lưu nhiều mảng | **`np.savez(p, a=x)`** rồi `np.load(p)["a"]` | Tệp **`.npz`** giống dict | [tr. 75–76](Th%E1%BB%B1c%20h%C3%A0nh%20NumPy%20ufunc%20t%E1%BB%87p%20v%C3%A0%20ng%E1%BA%ABu%20nhi%C3%AAn.md) |
| Ngẫu nhiên tái tạo | `rng = np.random.default_rng(seed)` | Cùng seed, cùng thứ tự gọi | [tr. 78–81](Th%E1%BB%B1c%20h%C3%A0nh%20NumPy%20ufunc%20t%E1%BB%87p%20v%C3%A0%20ng%E1%BA%ABu%20nhi%C3%AAn.md) |
| Series từ dict | **`pd.Series(d, index=[...])`** | Nhãn thiếu → NaN | [tr. 93–95](10%20Gi%E1%BB%9Bi%20thi%E1%BB%87u%20Pandas%20v%C3%A0%20Series.md) |
| Một ô nhanh | `df.at[nhãn, "c"]`, `df.iat[i, j]` | at nhãn, iat vị trí | [tr. 136](11%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt.md) |
| Gán cột Series | `df["c"] = pd.Series(v, index=[...])` | Căn index, thiếu NaN | [tr. 137–139](11%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt.md) |
| Index | `idx.union`, **`idx.delete(i)`**, **`idx.drop(v)`** | Trả Index mới | [tr. 145](04%20Index%20v%C3%A0%20c%C4%83n%20ch%E1%BB%89nh%20Pandas.md) |

> **info** Mở rộng
> **`s.value_counts()`**, `idx.has_duplicates`, **`a.flatten()`** ở bảng trên không có trong slide Lec3.

Nguồn Lec 3 · NumPy và Lec 3 · Pandas. Thẻ nhớ: Thẻ nhớ chương 3.
