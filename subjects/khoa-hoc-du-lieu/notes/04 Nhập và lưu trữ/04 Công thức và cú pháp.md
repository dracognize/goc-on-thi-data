# Công thức và cú pháp · Chương 4

> **abstract** Tóm tắt
> Bảng tra cuối chương. Trước khi gọi hàm: nhận diện **nguồn** (tệp, chuỗi, URL, CSDL) và **định dạng**. Sau khi gọi: kiểm tra **kiểu trả về** (DataFrame, list, dict, str, TextFileReader).

[![Chọn hàm đọc theo nguồn dữ liệu](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Ch%E1%BB%8Dn%20h%C3%A0m%20%C4%91%E1%BB%8Dc%20theo%20ngu%E1%BB%93n%20d%E1%BB%AF%20li%E1%BB%87u.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Ch%E1%BB%8Dn%20h%C3%A0m%20%C4%91%E1%BB%8Dc%20theo%20ngu%E1%BB%93n%20d%E1%BB%AF%20li%E1%BB%87u.excalidraw.md)

## 1. Các hàm đọc phổ biến trong pandas

Nguồn tr. 119.

[![C4 04 Công thức và cú pháp – bảng 1](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2004%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2004%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Hàm | Mô tả |
> | --- | --- |
> | **`read_csv`** | Đọc tệp CSV, phân tách bằng dấu phẩy (mặc định) |
> | **`read_table`** | Đọc dữ liệu phân tách bằng **tab** `\t` (mặc định) |
> | **`read_fwf`** | Đọc dữ liệu **độ rộng cột cố định** (fixed-width, không có ký tự phân tách) |
> | `read_clipboard` | Đọc từ **clipboard** (tiện khi sao chép bảng từ web) |
> | **`read_excel`** | Đọc tệp Excel (XLS/XLSX) |
> | **`read_json`** | Đọc dữ liệu JSON |
> | **`read_html`** | Đọc **tất cả** bảng trong tài liệu HTML |
> | `read_xml` | Đọc bảng từ tệp XML |
> | `read_sql` | Đọc kết quả truy vấn SQL vào DataFrame |

> **example** `read_table` và `read_fwf` (đã chạy)
> ```python
> from io import StringIO
> pd.read_table(StringIO("a\tb\n1\t2\n")).shape          # (1, 2)
> pd.read_fwf(StringIO("id  ten \n001 An  \n002 Binh\n"), widths=[4, 4], dtype={"id": str})
> #     id   ten
> # 0  001    An
> # 1  002  Binh
> ```

## 2. Kiểu trả về — câu thi hay hỏi

[![C4 04 Công thức và cú pháp – bảng 2](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2004%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2004%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.md)

> **note** Bảng dạng chữ
> | Lệnh | Trả về |
> | --- | --- |
> | **`pd.read_csv(path)`** | DataFrame |
> | **`pd.read_csv(path, chunksize=n)`** | `TextFileReader` (lặp ra từng DataFrame) |
> | **`df.to_csv()`** / **`df.to_json()`** (không đường dẫn) | `str` |
> | **`json.loads(s)`** | dict / list (theo JSON gốc) |
> | **`json.dumps(obj)`** | `str` |
> | **`pd.read_html(...)`** | **list** DataFrame |
> | **`pd.read_excel(path, sheet_name=None)`** | **dict** tên sheet → DataFrame |
> | **`pd.ExcelFile(path)`** | **`ExcelFile`** (có **`.sheet_names`**, **`.parse`**) |
> | **`requests.get(url)`** | `Response` (**`.status_code`**, **`.text`**, **`.content`**, **`.json()`**) |
> | **`cursor.fetchall()`** | list các tuple |

## 3. Cú pháp theo tác vụ

| Tác vụ | Cú pháp | Kiểm tra |
| --- | --- | --- |
| CSV dùng `;`, giữ mã có số 0 | **`pd.read_csv(p, sep=';', dtype={'id': str})`** | **`shape`**, `dtypes` |
| CSV không tiêu đề | **`pd.read_csv(p, header=None, names=[...])`** | tên cột |
| Index phân cấp | **`pd.read_csv(p, index_col=['key1','key2'])`** | **`df.index.nlevels`** |
| Khoảng trắng không đều | **`pd.read_csv(p, sep=r'\s+')`** | số cột |
| Bỏ dòng | *`skiprows=[0,2,3]`* / *`skiprows=2`* / *`skipfooter=1`* | số hàng |
| Quy ước thiếu riêng | *`na_values={'col': ['?']}, keep_default_na=False`* | **`isna().sum()`** |
| Tỉ lệ thiếu | `(df.isna().mean() * 100).round(1)` | |
| Tệp lớn | *`nrows=5`*; *`chunksize=1000`*; *`iterator=True`* + **`get_chunk(n)`** | |
| Ghi CSV | **`df.to_csv(p, index=False, sep=';', na_rep='NULL', columns=[...])`** | đọc lại |
| JSON ↔ Python | **`json.loads(s)`**, **`json.dumps(obj, ensure_ascii=False, indent=4)`** | **`type(...)`** |
| JSON Lines | **`pd.read_json(p, lines=True)`** | |
| Ghi JSON | **`df.to_json(p, orient='records', indent=4, force_ascii=False)`** | orient |
| Excel nhiều sheet | `x = pd.ExcelFile(p); x.parse(sheet_name='Sheet2', index_col=0)` | `x.sheet_names` |
| Ghi Excel | `with pd.ExcelWriter(p) as w: df.to_excel(w, sheet_name='S1')` | |
| Bảng HTML | `pd.read_html(src, match=..., attrs={'id': ...})[k]` | **`len(tables)`** |
| RSS | **`BeautifulSoup(res.content, 'xml').find_all('item')`** | thẻ thiếu |
| API | `r = requests.get(url); r.status_code == 200; r.json()` | khóa bản ghi |
| SQLite | `con = sqlite3.connect(f); con.executemany(sql, rows); con.commit()` | |
| Truy vấn → bảng | **`pd.DataFrame(cur.fetchall(), columns=[x[0] for x in cur.description])`** hoặc **`pd.read_sql(sql, con)`** | |

## 4. Công thức

- Tỉ lệ thiếu của cột: $p = \dfrac{\#\text{NaN}}{n}\times 100\%$ — `df.isna().mean()*100`.
- Số phần khi đọc theo chunk: $\lceil N / \text{chunksize} \rceil$ (N = số dòng dữ liệu).
- Số dòng còn sau *`skiprows=k`* (số nguyên) và có tiêu đề: $N_{\text{tệp}} - k - 1$.

[Mục lục chương 4](00%20M%E1%BB%A5c%20l%E1%BB%A5c.md) · Thẻ nhớ: Thẻ nhớ chương 4
