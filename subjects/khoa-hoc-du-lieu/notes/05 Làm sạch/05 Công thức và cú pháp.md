# Công thức và cú pháp · Chương 5

Tra nhanh theo mục tiêu. Với mỗi dòng: chọn cột cần xử lý, kiểm tra số hàng/ô trước và sau, nói được vì sao chọn cách đó. Bài đầy đủ: [01 Thiếu và trùng](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) · [Thực hành thêm - Điền dữ liệu bằng mô hình](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) · [03 Chuẩn hóa dữ liệu](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) · [04 Chuỗi và mã hóa phân loại](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md).

## Dữ liệu thiếu

| Tác vụ | Cú pháp | Trả về / ghi nhớ | Slide |
| --- | --- | --- | --- |
| Mặt nạ thiếu | **`df.isna()`** = **`df.isnull()`** | Boolean DataFrame | tr. 11 |
| Mặt nạ có dữ liệu | **`df.notna()`** = **`df.notnull()`** | Boolean DataFrame | tr. 11 |
| Đếm theo cột | **`df.isna().sum()`** | Series số | tr. 14 |
| Cột nào thiếu | **`df.isna().any()`** | Boolean Series | tr. 15 |
| Tổng ô thiếu | **`df.isna().sum().sum()`** | Một số | tr. 16 |
| Tỷ lệ % | `df.isnull().sum() / len(df) * 100` | Series % | tr. 35 |
| Bỏ hàng/cột | **`df.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)`** | *`axis=1`* bỏ cột · *`how='all'`* · *`thresh`* = số ô **có** dữ liệu tối thiểu | tr. 18 |
| Điền cố định | **`df.fillna({'Tuổi': 0, 'Phòng ban': 'Chưa xác định'})`** | Dict theo cột | tr. 25 |
| Điền mean / median | **`s.fillna(s.mean())`**, **`s.fillna(s.median())`** | Median bền với outlier | tr. 26 |
| Điền mode | **`s.fillna(s.mode()[0])`** | Nhớ `[0]` | tr. 28 |
| ffill / bfill | **`df.fillna(method='ffill')`** · `'bfill'` (mới: **`df.ffill()`**) | Lấy giá trị trước / sau | tr. 29 |
| KNN | **`KNNImputer(n_neighbors=2, weights='uniform').fit_transform(X)`** | Mảng NumPy | tr. 62 |
| Random Forest | **`RandomForestRegressor(n_estimators=10, random_state=42, max_depth=3)`** | **`.fit(X, y)`**, **`.predict(X)`**, **`.feature_importances_`** | tr. 48 |
| Ghi dự đoán | `df.loc[df['Tuổi'].isna(), 'Tuổi'] = pred` | Theo mặt nạ | tr. 51 |

## Dữ liệu trùng

| Tác vụ | Cú pháp | Ghi nhớ | Slide |
| --- | --- | --- | --- |
| Cờ trùng | **`df.duplicated()`** | Lần đầu False, các lần sau True | tr. 75 |
| Xem hàng trùng | `df[df.duplicated()]` | | tr. 76 |
| Đếm | **`df.duplicated().sum()`** | Số hàng **thừa** | tr. 76 |
| Xóa | **`df.drop_duplicates(subset=None, keep='first', inplace=False, ignore_index=False)`** | *`keep='last'`* / `False` (bỏ hết) | tr. 78 |

## Scale



> **note** Bảng dạng chữ
> | Scaler | Công thức | Thống kê dùng | Outlier |
> | --- | --- | --- | --- |
> | **`MinMaxScaler()`** | $\dfrac{x-x_{\min}}{x_{\max}-x_{\min}}$ | min, max | Rất nhạy |
> | **`StandardScaler()`** | $\dfrac{x-\mu}{\sigma}$ | mean, std (mẫu số $n$) | Rất nhạy (ít hơn MinMax) |
> | **`RobustScaler()`** | $\dfrac{x-\text{median}}{Q_3-Q_1}$ | median, IQR | Ít nhạy |

**`scaler.fit_transform(X_train)`** rồi **`scaler.transform(X_test)`**.

## Chuỗi và regex



> **note** Bảng dạng chữ
> | Tác vụ | Cú pháp | Trả về |
> | --- | --- | --- |
> | Đổi kiểu | **`astype('int64')`**, **`astype('float64')`**, **`pd.to_datetime(s)`**, **`astype('category')`** | Cột kiểu mới |
> | Chữ | `.str.lower()`, **`.upper()`**, **`.title()`**, **`.swapcase()`** | Chuỗi |
> | Làm sạch | `.str.strip()`, `.str.replace(a, b)` | Chuỗi |
> | Tách/nối | `.str.split(' ')` (list) · `.str.cat(sep='_')` (một chuỗi) · `.str.repeat(n)` | |
> | Kiểm tra | `.str.contains()`, **`.startswith()`**, **`.endswith()`**, **`.islower()`**, **`.isupper()`**, **`.isnumeric()`** | Boolean |
> | Đếm/tìm | `.str.len()`, **`.count(p)`**, **`.find(p)`** (−1 nếu không có), **`.findall(p)`** (list) | |
> | Regex | `.str.extract(r'(\d+)', expand=False)`, `.str.replace(p, r, regex=True)` | Nhóm đầu tiên / NaN |
> | Ký hiệu | `\d` số · `\w` chữ-số-_ · `\s` trắng · `+` ≥1 · `*` ≥0 · `?` 0–1 · `[]` nhóm · `^` đầu · `$` cuối | |

## Phân loại và mã hóa



> **note** Bảng dạng chữ
> | Tác vụ | Cú pháp | Ghi nhớ |
> | --- | --- | --- |
> | Categorical có thứ tự | **`pd.Categorical(values, categories=[...], ordered=True)`** | **`.codes`**, **`.min()`**, **`.max()`** |
> | Label Encoding | **`LabelEncoder().fit_transform(s)`** | `classes_` sắp theo bảng chữ cái |
> | One-hot pandas | **`pd.get_dummies(df, columns=[...], prefix=[...])`** | *`drop_first=True`*, *`dtype=int`* |
> | One-hot sklearn | **`OneHotEncoder(sparse_output=False, drop='first')`** | **`get_feature_names_out(cols)`** |
> | Mã thứ tự tường minh | **`s.map({'thấp': 0, 'vừa': 1, 'cao': 2})`** (Mở rộng) | Nhãn lạ → NaN |

## Mở rộng: rời rạc hóa (dạng câu F511)

> **info** Mở rộng
> **`pd.cut(s, bins=[0, 18, 60, 100])`** chia theo **mốc cố định**, khoảng mặc định **đóng phải** `(a, b]`. **`pd.qcut(s, q=4)`** chia theo **phân vị**, mỗi nhóm số phần tử xấp xỉ nhau. **`s.replace({'a': 'b'})`** đổi giá trị, giá trị không có trong từ điển được **giữ nguyên** (khác `map` cho NaN).

**Áp dụng ở** F511 Rời rạc hóa và thay thế giá trị · F510 Kiểu dữ liệu cột.

Mục lục chương 5 · Thẻ nhớ chương 5
