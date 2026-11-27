# JSON và Excel

> **abstract** Tóm tắt
> - **JSON** (JavaScript Object Notation): văn bản dễ đọc cho người và máy, dùng được với hầu hết ngôn ngữ, là **định dạng chuẩn của API web**. Hai cấu trúc: **object** `{}` (cặp key–value) và **array** `[]` (danh sách).
> - Thư viện **`json`**: **`json.loads(chuỗi)`** → đối tượng Python; **`json.dumps(đối tượng)`** → chuỗi JSON.
> - Pandas: **`pd.read_json(...)`** → DataFrame/Series; **`df.to_json(orient=...)`** → JSON.
> - **Excel**: **`pd.ExcelFile(...).parse(sheet_name=...)`** hoặc **`pd.read_excel(...)`**; ghi bằng **`pd.ExcelWriter`** + **`to_excel`**.

[![JSON qua lại Python và orient](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/JSON%20qua%20l%E1%BA%A1i%20Python%20v%C3%A0%20orient.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/JSON%20qua%20l%E1%BA%A1i%20Python%20v%C3%A0%20orient.excalidraw.md)

## Phần A · JSON

### 1. JSON là gì

Nguồn tr. 41, tr. 42.

```json
{ "name": "Nguyen Van A",
  "age": 25,
  "isStudent": true,
  "hobbies": ["reading", "coding", "traveling"],
  "address": { "street": "123 Le Loi", "city": "Hanoi" } }
```

- **Key**: `"name"`, `"age"`, `"isStudent"`, `"hobbies"`, `"address"`.
- **Value**: `"Nguyen Van A"`, `25`, `true`, mảng `["reading", …]`, và **object lồng** `{"street": …, "city": …}`.

### 2. Object và Array

Nguồn tr. 43, tr. 44.

[![C4 02 JSON và Excel – bảng 1](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | | Object | Array |
> | --- | --- | --- |
> | Bao bởi | `{ }` | `[ ]` |
> | Thành phần | cặp `key: value`, cách nhau dấu phẩy | các giá trị, cách nhau dấu phẩy |
> | Key | **chuỗi trong nháy kép** `"..."` | không có key |
> | Giá trị cho phép | string `"Hello"`, number `42`/`3.14`, boolean `true`/`false`, array, object, `null` | như bên trái, mọi kiểu JSON |

> **warning** Dễ nhầm · JSON khác dict Python
> JSON bắt buộc **nháy kép**; `{'a': 1}` không hợp lệ. Viết `true/false/null` chữ thường, Python là `True/False/None`.

### 3. Tệp và chuỗi JSON mẫu

Nguồn tr. 45, tr. 46.

```python
obj = """{"name": "Wes",
 "cities_lived": ["Akron", "Nashville", "New York", "San Francisco"],
 "pet": null,
 "siblings": [{"name": "Scott", "age": 34, "hobbies": ["guitars", "soccer"]},
              {"name": "Katie", "age": 42, "hobbies": ["diving", "art"]}]}"""
```

Cùng nội dung có thể nằm trong tệp `data.json` hoặc trong chuỗi Python ba nháy `"""..."""`.

### 4. json.loads() – chuỗi → Python

Nguồn tr. 47, tr. 48.

```python
json.loads(s, *, cls=None, object_hook=None, parse_float=None,
           parse_int=None, parse_constant=None, object_pairs_hook=None, **kw)
```

[![C4 02 JSON và Excel – bảng 2](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.md)

> **note** Bảng dạng chữ
> | Tham số | Kiểu | Mặc định | Chức năng | Ví dụ |
> | --- | --- | --- | --- | --- |
> | *`s`* | str | bắt buộc | Chuỗi JSON cần parse | **`json.loads('{"a":1}')`** |
> | *`cls`* | JSONDecoder | None | Decoder tùy chỉnh | *`cls=MyDecoder`* |
> | *`object_hook`* | callable | None | Xử lý mỗi dict sau parse (dict → đối tượng khác) | *`object_hook=lambda d: MyClass(**d)`* |
> | *`object_pairs_hook`* | callable | None | Xử lý danh sách cặp (key, value), giữ thứ tự key | *`object_pairs_hook=dict`* |
> | *`parse_float`* | callable | float | Hàm xử lý số thực | *`parse_float=Decimal`* |
> | *`parse_int`* | callable | int | Hàm xử lý số nguyên | *`parse_int=str`* |
> | *`parse_constant`* | callable | (xem dưới) | Xử lý `NaN`, `Infinity`, `-Infinity` | *`parse_constant=lambda x: "INVALID"`* |
> | `**kw` | – | – | Truyền thêm cho JSONDecoder, ít dùng | |

```python
from decimal import Decimal
print(json.loads('{"x":1.23}', parse_float=Decimal))   # {'x': Decimal('1.23')}
print(json.loads('{"x":123}', parse_int=str))          # {'x': '123'}
print(json.loads('NaN', parse_constant=lambda x: "INVALID"))  # INVALID
```

> **info** Mở rộng
> Slide ghi mặc định của *`parse_constant`* là "lỗi nếu có". Thực tế Python 3 mặc định **chấp nhận** `NaN` và trả **`float('nan')`**: **`json.loads('NaN')`** → `nan` (đã chạy kiểm chứng).

#### Bảng chuyển JSON → Python

Nguồn tr. 49.

[![C4 02 JSON và Excel – bảng 3](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%203.excalidraw.md)

> **note** Bảng dạng chữ
> | JSON | Python |
> | --- | --- |
> | object `{}` | `dict` |
> | array `[]` | `list` |
> | string `"abc"` | `str` |
> | number `123` / `1.5` | `int` hoặc `float` |
> | `true` / `false` | `True` / `False` |
> | `null` | `None` |

```python
json_str = '{"name": "An", "age": 21, "is_student": true, "scores": [8.5, 9.0, 7.5], "address": null}'
data = json.loads(json_str)
print(type(data))        # <class 'dict'>
print(data["name"])      # An
print(data["scores"])    # [8.5, 9.0, 7.5]
print(data["address"])   # None
```

Nguồn tr. 50. Với chuỗi `obj` của Wes (tr. 51): **`type(json.loads(obj))`** là `dict`, `"pet": null` thành `'pet': None`.

### 5. json.dumps() – Python → chuỗi

Nguồn tr. 52, tr. 53.

```python
json.dumps(obj, *, skipkeys=False, ensure_ascii=True, check_circular=True,
           allow_nan=True, cls=None, indent=None, separators=None,
           default=None, sort_keys=False, **kw)
```

[![C4 02 JSON và Excel – bảng 4](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%204.excalidraw.md)

> **note** Bảng dạng chữ
> | Tham số | Mặc định | Ý nghĩa |
> | --- | --- | --- |
> | `obj` | bắt buộc | Đối tượng Python cần chuyển |
> | *`skipkeys`* | False | True: bỏ qua key không phải str/int/float/bool/None thay vì báo lỗi |
> | *`ensure_ascii`* | **True** | True: escape ký tự non-ASCII (tiếng Việt → `\uXXXX`). False: giữ nguyên Unicode |
> | *`check_circular`* | True | Kiểm tra vòng tham chiếu |
> | *`allow_nan`* | True | Cho phép NaN, Infinity. False → báo lỗi |
> | *`cls`* | None | Encoder tùy chỉnh |
> | *`indent`* | None | Thụt lề, in đẹp (pretty-print) |
> | *`separators`* | `(', ', ': ')` | Đổi ký tự phân cách, `(',', ':')` cho JSON gọn |
> | *`default`* | None | Hàm serialize đối tượng không được hỗ trợ |
> | *`sort_keys`* | False | True: sắp key theo thứ tự từ điển |

> **example** Năm biến thể của `dumps` (tr. 54, đã chạy)
> ```python
> data = {"name": "An Bình", "age": 21, "is_student": True,
>         "scores": [8.5, 9.0, None], "gpa": float("8.75")}
> print(json.dumps(data))
> # {"name": "An Bình", "age": 21, "is_student": true, "scores": [8.5, 9.0, null], "gpa": 8.75}
> print(json.dumps(data, ensure_ascii=False))
> # {"name": "An Bình", "age": 21, "is_student": true, "scores": [8.5, 9.0, null], "gpa": 8.75}
> print(json.dumps(data, separators=(",", ":"), ensure_ascii=False))
> # {"name":"An Bình","age":21,"is_student":true,"scores":[8.5,9.0,null],"gpa":8.75}
> print(json.dumps(data, sort_keys=True, ensure_ascii=False))
> # {"age": 21, "gpa": 8.75, "is_student": true, "name": "An Bình", "scores": [8.5, 9.0, null]}
> print(json.dumps(data, indent=4, ensure_ascii=False))   # mỗi key một dòng, thụt 4 dấu cách
> ```
> Để ý: `True` → `true`, `None` → `null`, `ì` → `ì` khi *`ensure_ascii=True`*.

**`json.dumps(result)`** với dict của Wes (tr. 55) cho `<class 'str'>` và `None` quay lại thành `null`.

```python
json.dumps(float("nan"))                  # 'NaN'  (allow_nan=True)
json.dumps(float("nan"), allow_nan=False) # ValueError: Out of range float values are not JSON compliant
json.dumps({(1, 2): 3}, skipkeys=True)    # '{}'   key tuple bị bỏ qua
```

> **tip** Mẹo thi · chữ **s**
> **`loads`**/**`dumps`** có **s = string**: làm việc với chuỗi. **`load`**/`dump` không có s: làm việc với **đối tượng tệp** (**`json.load(f)`**, **`json.dump(obj, f)`**).
>
> | Đang có | Dùng | Ra |
> | --- | --- | --- |
> | Chuỗi JSON | **`json.loads(text)`** | dict/list |
> | Tệp đã mở | **`json.load(f)`** | dict/list |
> | Đối tượng Python | **`json.dumps(obj)`** | str |
> | Đối tượng + tệp | **`json.dump(obj, f)`** | ghi tệp |

### 6. JSON → DataFrame

Nguồn tr. 56.

Cách đơn giản: truyền **danh sách dict** vào **`pd.DataFrame`**, chọn trường cần thiết.

```python
result = json.loads(obj)
siblings = pd.DataFrame(result["siblings"], columns=["name", "age"])
print(siblings)
#     name  age
# 0  Scott   34
# 1  Katie   42
```

Cột `hobbies` bị bỏ vì không có trong *`columns`*.

> **info** Mở rộng · `pd.json_normalize`
> Khi mỗi bản ghi có dict lồng, **`pd.json_normalize(records)`** trải phẳng: `{"id":"001","profile":{"score":8}}` → cột `id`, `profile.score`.

### 7. pd.read_json

Nguồn tr. 57, tr. 58.

```python
pd.read_json(path_or_buf=None, orient=None, typ='frame', dtype=True,
             convert_axes=None, convert_dates=True, keep_default_dates=True,
             precise_float=False, date_unit=None, encoding=None,
             lines=False, chunksize=None, compression='infer')
```

[![C4 02 JSON và Excel – bảng 5](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%205.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%205.excalidraw.md)

> **note** Bảng dạng chữ
> | Tham số | Ý nghĩa |
> | --- | --- |
> | *`path_or_buf`* | Đường dẫn tệp JSON, URL hoặc chuỗi JSON |
> | *`orient`* | Cách tổ chức JSON: `'records'`, `'split'`, `'index'`, `'columns'`, `'values'` |
> | *`typ`* | Kiểu trả về: `'frame'` (DataFrame) hoặc `'series'` |
> | *`dtype`* | Tự ép kiểu (mặc định True) |
> | *`convert_dates`* | Tự nhận và chuyển cột ngày tháng |
> | *`lines`* | `True` khi **mỗi dòng là một object** (JSON Lines) |
> | *`compression`* | Đọc tệp nén `'zip'`, `'gzip'`, `'bz2'`… |
> | *`encoding`* | `"utf-8"` hoặc `"utf-8-sig"` cho tiếng Việt |

Đã chạy:

```python
from io import StringIO
print(pd.read_json(StringIO('[{"a": 1, "b": 2, "c": 3},{"a": 4, "b": 5, "c": 6},{"a": 7, "b": 8, "c": 9}]')))
#    a  b  c          ← tr. 59: example.json là list các object
# 0  1  2  3
# 1  4  5  6
# 2  7  8  9
print(pd.read_json(StringIO('{"name":"An","age":21}\n{"name":"Bình","age":22}\n'), lines=True))
#    name  age        ← tr. 60: data.json mỗi dòng một object
# 0    An   21
# 1  Bình   22
```

Nguồn tr. 59, tr. 60.

**Ví dụ `student.json`** (tr. 61, tr. 62): 10 sinh viên, cột `ten, diem_toan, diem_van, diem_anh, diem_ly`. Giá trị `null` thành `NaN`. Sau đó **`df_json.dropna()`** **xóa các hàng có NaN** → còn 5 hàng (An, Dung, Ha, Khanh, Ngoc).

> **warning** Dễ nhầm
> Tệp JSON Lines (mỗi dòng một object, không có `[ ]` bao ngoài) mà quên *`lines=True`* → lỗi "Trailing data". Truyền chuỗi JSON trực tiếp nên bọc **`StringIO(...)`** (pandas mới cảnh báo khi đưa chuỗi thô).

### 8. Ghi JSON – to_json

Nguồn tr. 64–67.

```python
DataFrame.to_json(path_or_buf=None, orient=None, date_format=None,
                  double_precision=10, force_ascii=True, date_unit='ms',
                  default_handler=None, lines=False, compression='infer',
                  index=True, indent=None, storage_options=None)
```

[![C4 02 JSON và Excel – bảng 6](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%206.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%2002%20JSON%20v%C3%A0%20Excel%20%E2%80%93%20b%E1%BA%A3ng%206.excalidraw.md)

> **note** Bảng dạng chữ
> | Tham số | Mô tả |
> | --- | --- |
> | *`path_or_buf`* | Tệp hoặc đối tượng tệp (vd `io.StringIO`). `None` → trả chuỗi JSON |
> | *`orient`* | Hình dạng JSON (bảng dưới) |
> | *`indent`* | Số dấu cách thụt lề, hay dùng 4 |
> | *`force_ascii`* | Mặc định True: ép ký tự không ASCII thành `\uXXXX`. Giữ tiếng Việt → *`force_ascii=False`* |

Với `df = pd.DataFrame({"col1":[1,3], "col2":[2,4]})` (đã chạy):

| *`orient`* | Kết quả | Dùng cho |
| --- | --- | --- |
| `'records'` | `[{"col1":1,"col2":2},{"col1":3,"col2":4}]` | Danh sách bản ghi, phổ biến nhất |
| `'split'` | `{"columns":["col1","col2"],"index":[0,1],"data":[[1,2],[3,4]]}` | Khôi phục DataFrame chính xác |
| `'index'` | `{"0":{"col1":1,"col2":2},"1":{"col1":3,"col2":4}}` | Index là key chính |
| `'columns'` | `{"col1":{"0":1,"1":3},"col2":{"0":2,"1":4}}` | Tên cột là key chính |
| `'values'` | `[[1,2],[3,4]]` | Chỉ giá trị, ít dùng |
| `'table'` | `{"schema":{"fields":[...]}, "data":[...]}` | Chuẩn JSON Table Schema, dễ tương tác SQL/API |

> **warning** Dễ nhầm · orient mặc định
> Slide ghi "records (Mặc định)". Thực tế với **DataFrame**, **`df.to_json()`** mặc định là **`'columns'`** (đã chạy: `{"col1":{"0":1,"1":3},...}`). Với Series mặc định là `'index'`. Khi đề nói "danh sách các bản ghi" → *`orient="records"`*.

> **example** Ghi danh sách sinh viên (tr. 67)
> ```python
> data = {"name": ["Nguyen Van A", "Le Thi B", "Tran Van C"],
>         "tuoi": [25, 30, 22],
>         "que_quan": ["Hanoi", "Ho Chi Minh", "Da Nang"]}
> df = pd.DataFrame(data)
> df.to_json("dssv.json", orient="records", indent=4)
> ```
> Tệp `dssv.json` là một mảng 3 object, mỗi object có *`name`*, `tuoi`, `que_quan`, thụt 4 dấu cách.
>
> Nếu có dấu: **`to_json(orient="records")`** cho `"Hà Nội"`; thêm *`force_ascii=False`* → `"Hà Nội"`.

## Phần B · Excel

### 9. Đọc Excel

Nguồn tr. 91–93.

Pandas đọc bảng trong tệp Excel (từ bản 2003) qua **`pd.ExcelFile`** hoặc **`pd.read_excel`**. Phương thức **`parse()`** của **`ExcelFile`** đọc **một sheet cụ thể** thành DataFrame.

```python
xlsx = pd.ExcelFile("./data/ex6.xlsx")
df_excel_sheet2 = xlsx.parse(sheet_name="Sheet2")   # bảng giá AAPL, MSFT, GOOGL, AMZN theo Datetime
df_excel_sheet1 = xlsx.parse(sheet_name="Sheet1")   # bảng điểm Ho va ten, Diem_Toan...
frame_excel_indexed = xlsx.parse(sheet_name="Sheet2", index_col=0)  # cột Datetime làm index
df = pd.read_excel("data/ex6.xlsx", sheet_name="Sheet2")            # chỉ 1 sheet
```

| Tình huống | Nên dùng | Lý do (tr. 93) |
| --- | --- | --- |
| Đọc **nhiều** sheet trong một tệp | **`pd.ExcelFile`** rồi **`.parse(...)`** | Mở tệp một lần → **nhanh hơn** |
| Chỉ một sheet | **`pd.read_excel(path, sheet_name=...)`** | Ngắn gọn |
| Mọi sheet | **`pd.read_excel(path, sheet_name=None)`** | Trả **dict** tên sheet → DataFrame (mở rộng) |

*`index_col=0`* (tr. 92) biến cột đầu (Datetime) thành index.

### 10. Ghi Excel

Nguồn tr. 94, tr. 95.

```mermaid
flowchart LR
    A[Chuẩn bị DataFrame<br/>từ Excel, CSV, JSON, web...] --> B[Tạo pd.ExcelWriter<br/>hoặc chỉ tên tệp]
    B --> C[df.to_excel writer,<br/>sheet_name, index, header]
    C --> D[writer.close<br/>hoặc with ... as writer]
    D --> E[Tệp Excel mới<br/>hoặc ghi đè tệp có sẵn]
```

```python
xlsx = pd.ExcelFile("./data/ex6.xlsx")
print(type(xlsx))                 # <class 'pandas.io.excel._base.ExcelFile'>
df_excel_sheet1 = xlsx.parse(sheet_name="Sheet1")
print(type(df_excel_sheet1))      # <class 'pandas.core.frame.DataFrame'>
writer1 = pd.ExcelWriter("./data/ex6_1.xlsx")
df_excel_sheet1.to_excel(writer1, sheet_name="Sh1_ex1")
writer1.close()                   # bắt buộc đóng, nếu không tệp chưa được ghi xong
```

> **warning** Dễ nhầm
> - **`ExcelFile`** dùng để **đọc**, **`ExcelWriter`** dùng để **ghi**.
> - Quên **`writer.close()`** → tệp hỏng hoặc rỗng. Dùng `with pd.ExcelWriter(...) as writer:` để tự đóng.
> - Mỗi **`to_excel`** vào cùng writer với *`sheet_name`* khác nhau → **nhiều sheet trong một tệp**.

### 11. Thư viện phụ trợ

Nguồn tr. 96.

`openpyxl` cho **`.xlsx`**, `xlrd` cho **`.xls`**. Cài: `pip install openpyxl xlrd`. Ví dụ chạy được đầy đủ ở [Thực hành Excel nhiều sheet và SQLAlchemy](Th%E1%BB%B1c%20h%C3%A0nh%20Excel%20nhi%E1%BB%81u%20sheet%20v%C3%A0%20SQLAlchemy.md).

## Tự kiểm tra

> **question** 1. `json.loads('{"ok": true, "x": null}')` cho gì?
> `{'ok': True, 'x': None}` kiểu `dict`.

> **question** 2. Muốn chuỗi JSON giữ nguyên "Hà Nội" thì cần tham số nào ở `json.dumps` và ở `to_json`?
> *`ensure_ascii=False`* (json.dumps) và *`force_ascii=False`* (to_json).

> **question** 3. `separators=(",", ":")` có tác dụng gì?
> Bỏ khoảng trắng sau dấu phẩy và dấu hai chấm → JSON gọn nhất.

> **question** 4. orient nào cho `{"index":[...],"columns":[...],"data":[...]}`?
> `'split'`.

> **question** 5. Tệp mỗi dòng một object JSON. Đọc bằng gì?
> **`pd.read_json(path, lines=True)`**.

> **question** 6. Cần đọc 3 sheet trong cùng tệp. Dùng gì cho nhanh?
> **`pd.ExcelFile(path)`** một lần rồi **`.parse(sheet_name=...)`** cho từng sheet.

**Áp dụng ở.** F404 Giải mã JSON và JSON Lines · F403 Đọc Excel và nhiều sheet · F402 Ghi tệp · bài mẫu [Giải mã JSON và phản hồi API](../09%20Luy%E1%BB%87n%20theo%20c%E1%BB%A5m/H%E1%BB%8D%20b%C3%A0i/Ch%C6%B0%C6%A1ng%204%20-%20Gi%E1%BA%A3i%20m%C3%A3%20JSON%20v%C3%A0%20ph%E1%BA%A3n%20h%E1%BB%93i%20API.md).

Trước: [Ghi CSV với to_csv](Ghi%20CSV%20v%E1%BB%9Bi%20to_csv.md) · Tiếp: [03 Web API XML và SQLite](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) · [Mục lục chương 4](00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
