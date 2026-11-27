# Thực hành Excel nhiều sheet và SQLAlchemy

Hai ví dụ này dùng dữ liệu tự tạo trên máy. Nguồn đối chiếu cho Excel là Lec 4, trang 93–96 và cho SQLAlchemy là Lec 4, trang 116–119. Các đoạn cần **pandas**, cùng **openpyxl** cho Excel hoặc **SQLAlchemy** cho ví dụ cơ sở dữ liệu dưới đây.

## Workbook, worksheet và engine

Một tệp **`.xlsx`** là **workbook**, có thể chứa nhiều **worksheet** (trang tính). Mỗi trang có tên như `Hang` hoặc `Kho`. Một **engine** là bộ đọc hoặc ghi hiểu định dạng tệp. Ví dụ dùng *`engine="openpyxl"`* khi làm việc với **`.xlsx`**.

[![C4 Thực hành Excel nhiều sheet và SQLAlchem – bảng 1](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%20Th%E1%BB%B1c%20h%C3%A0nh%20Excel%20nhi%E1%BB%81u%20sheet%20v%C3%A0%20SQLAlchem%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C4%20Th%E1%BB%B1c%20h%C3%A0nh%20Excel%20nhi%E1%BB%81u%20sheet%20v%C3%A0%20SQLAlchem%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Việc cần làm | API | Đầu ra hoặc tác động |
> | --- | --- | --- |
> | Đọc một trang | **`pd.read_excel(path, sheet_name="Hang")`** | Một DataFrame |
> | Đọc toàn bộ các trang | **`pd.read_excel(path, sheet_name=None)`** | Dict từ tên trang sang DataFrame |
> | Mở tệp để biết tên và chọn vài trang | **`pd.ExcelFile(path)`** | Đối tượng có **`.sheet_names`** và **`.parse(...)`** |
> | Ghi nhiều trang vào cùng một tệp | `with pd.ExcelWriter(path, engine="openpyxl") as writer:` | Từng lời gọi **`df.to_excel(writer, sheet_name=...)`** ghi một trang |

### Ví dụ theo dấu hai trang tính

```python
from pathlib import Path
from tempfile import TemporaryDirectory
import pandas as pd

hang = pd.DataFrame({"ma": ["001", "002"], "ten": ["Vở", "Bút"]})
kho = pd.DataFrame({"ma": ["001", "002"], "ton": [7, 3]})

with TemporaryDirectory() as thu_muc:
    tep = Path(thu_muc) / "hang_va_kho.xlsx"

    with pd.ExcelWriter(tep, engine="openpyxl") as writer:
        hang.to_excel(writer, sheet_name="Hang", index=False)
        kho.to_excel(writer, sheet_name="Kho", index=False)

    with pd.ExcelFile(tep, engine="openpyxl") as workbook:
        print(workbook.sheet_names)  # ['Hang', 'Kho']
        danh_muc = workbook.parse("Hang", dtype={"ma": str})
        ton_kho = workbook.parse("Kho", dtype={"ma": str})
        print(danh_muc["ma"].tolist())  # ['001', '002']
        print(ton_kho["ton"].sum())     # 10
```

1. Tạo hai bảng trong bộ nhớ. Cột `ma` lưu chuỗi có số 0 ở đầu.
2. Mở một writer, ghi hai trang vào **cùng** workbook. *`index=False`* bỏ chỉ số hàng hiện có khi ghi.
3. Thoát khối writer để hoàn tất kết xuất, rồi mở workbook và xem danh sách tên.
4. Đọc theo tên sheet và yêu cầu `ma` là chuỗi. Kiểm tra cả hai bảng trước khi dùng khóa để ghép.

> **warning** Số 0 đầu phụ thuộc dữ liệu được lưu
> Ví dụ lưu mã 001 dưới dạng **chuỗi**. Nếu ô Excel lưu số 1 và chỉ hiển thị nó thành 001 nhờ định dạng hiển thị, ép kiểu sang chuỗi thường chỉ cho "1". Cần quy ước độ rộng mã hoặc lưu cột dưới dạng văn bản từ nguồn.

> **question** Khi đề yêu cầu đọc đúng một sheet, API ngắn nhất là gì?
> Dùng **`pd.read_excel(tep, sheet_name="Kho")`**. Khi cần xem tên rồi đọc nhiều sheet theo lựa chọn, dùng **`ExcelFile`** và **`.parse`**.

## SQLAlchemy Core, ORM và bảng kết quả

Slide giới thiệu **SQLAlchemy Core** và **ORM**. Core cho phép làm việc với kết nối, lệnh SQL và bảng. ORM cho phép ánh xạ bảng sang lớp Python để thao tác qua đối tượng và session. Khi đích là một DataFrame từ truy vấn cho bài nhập dữ liệu, ví dụ Core dưới đây đủ để theo rõ từng bước.

- **Engine** biết loại cơ sở dữ liệu và cách mở kết nối.
- **Connection** là kênh để chạy câu lệnh.
- **Transaction** là nhóm thao tác hoàn tất hoặc được hoàn tác cùng nhau.
- **Tham số truy vấn** là dữ liệu truyền tách khỏi câu SQL. `:ma` là chỗ nhận giá trị `ma`. Tên bảng và tên cột vẫn do người viết câu SQL chỉ định.

### Ví dụ chạy trên SQLite trong bộ nhớ

```python
import pandas as pd
from sqlalchemy import create_engine, text

engine = create_engine("sqlite+pysqlite:///:memory:")
try:
    with engine.begin() as con:
        con.execute(text("CREATE TABLE kho (ma TEXT PRIMARY KEY, ton INTEGER)"))
        con.execute(
            text("INSERT INTO kho (ma, ton) VALUES (:ma, :ton)"),
            [{"ma": "001", "ton": 7}, {"ma": "002", "ton": 3}],
        )
        truy_van = text("SELECT ma, ton FROM kho WHERE ton >= :muc ORDER BY ma")
        ket_qua = pd.read_sql_query(truy_van, con, params={"muc": 5})
        print(ket_qua.to_dict("records"))  # [{'ma': '001', 'ton': 7}]
finally:
    engine.dispose()
```

1. `CREATE TABLE` định nghĩa hai cột. `PRIMARY KEY` yêu cầu mã duy nhất.
2. `INSERT` nhận hai bộ tham số và lưu hai hàng.
3. `SELECT` chỉ giữ hàng có tồn kho ít nhất bằng mức truyền vào. Pandas biến kết quả thành DataFrame.
4. Khối **`engine.begin()`** quản lý kết nối và giao dịch. Cơ sở dữ liệu ví dụ ở trong bộ nhớ. Giữ các thao tác trong cùng kết nối để cùng nhìn thấy dữ liệu đã tạo.

> **question** Đổi mức lọc thành 3 thì còn gì?
> Có hai hàng 001 và 002. Phép so sánh dùng `>=`, nên 3 cũng được giữ.

Nếu cần thực hành ngay bằng thư viện chuẩn Python, xem ví dụ `sqlite3` ở [note Web, API, XML và SQLite](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md).
