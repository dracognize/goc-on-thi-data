# Chương 4 · Nhập và lưu trữ

**Bắt đầu từ số 0.** Dữ liệu trên máy thường là tệp hoặc phản hồi mạng. Đọc dữ liệu nghĩa là chuyển nội dung thành đối tượng Python hay bảng Pandas để kiểm tra và tính toán. Ghi dữ liệu làm ngược lại. Với mỗi ví dụ hãy chỉ ra đầu vào, hàm đọc, đối tượng trả về và dấu hiệu đọc sai.

Slide gốc: Lec 4 – Nhập và lưu trữ dữ liệu. Mục tiêu bài giảng (tr. 2): đọc/ghi tệp văn bản (CSV, JSON, XML), tải từ CSDL (SQL, SQLite), lấy dữ liệu qua mạng (API web, nguồn trực tuyến).

## Thứ tự đọc

1. [01 CSV và schema](01%20CSV%20v%C3%A0%20schema.md) — đọc CSV bằng **`read_csv`** (4.1.1)
2. [Ghi CSV với to_csv](Ghi%20CSV%20v%E1%BB%9Bi%20to_csv.md) — ghi CSV (4.1.2)
3. [02 JSON và Excel](02%20JSON%20v%C3%A0%20Excel.md) — JSON đọc/ghi (4.1.3–4.1.4) và Excel (4.3)
4. [03 Web API XML và SQLite](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) — web, XML/RSS (4.2), API (4.4), CSDL (4.5)
5. [Thực hành Excel nhiều sheet và SQLAlchemy](Th%E1%BB%B1c%20h%C3%A0nh%20Excel%20nhi%E1%BB%81u%20sheet%20v%C3%A0%20SQLAlchemy.md) — ví dụ chạy được, mở rộng
6. [04 Công thức và cú pháp](04%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md) — bảng tra cuối chương (tr. 119)
7. [05 Tự kiểm tra](05%20T%E1%BB%B1%20ki%E1%BB%83m%20tra.md) → Thẻ nhớ chương 4 (plugin Spaced Repetition, tag `#flashcards/chuong-4`)

## Bản đồ chương



## Phủ slide

| Trang | Chủ đề | Note |
| --- | --- | --- |
| 1 | Bìa | không có nội dung thi |
| 2 | Mục tiêu bài giảng | Mục lục này |
| 3–6, 33, 40, 63, 68, 90, 97, 103 | Trang mục lục, chuyển mục | không có nội dung thi |
| 7–8 | CSV khác Excel, định nghĩa CSV | [01 · mục 1](01%20CSV%20v%C3%A0%20schema.md) |
| 9–13 | Cú pháp và bảng tham số read_csv | [01 · mục 2](01%20CSV%20v%C3%A0%20schema.md) |
| 14–15 | Ví dụ cơ bản, đọc ex1 | [01 · mục 3](01%20CSV%20v%C3%A0%20schema.md) |
| 16–22 | header, names, index_col, vai trò index | [01 · mục 4](01%20CSV%20v%C3%A0%20schema.md) |
| 23 | sep=r"\s+" | [01 · mục 5](01%20CSV%20v%C3%A0%20schema.md) |
| 24 | skiprows | [01 · mục 6](01%20CSV%20v%C3%A0%20schema.md) |
| 25–28 | Giá trị thiếu, na_values, keep_default_na | [01 · mục 7](01%20CSV%20v%C3%A0%20schema.md) |
| 29–32 | nrows, chunksize, get_chunk | [01 · mục 8](01%20CSV%20v%C3%A0%20schema.md) |
| 34–39 | to_csv | [to_csv · mục 1–4](Ghi%20CSV%20v%E1%BB%9Bi%20to_csv.md) |
| 41–46 | JSON, object, array, dữ liệu mẫu | [02 · mục 1–3](02%20JSON%20v%C3%A0%20Excel.md) |
| 47–51 | json.loads, bảng JSON → Python | [02 · mục 4](02%20JSON%20v%C3%A0%20Excel.md) |
| 52–55 | json.dumps | [02 · mục 5](02%20JSON%20v%C3%A0%20Excel.md) |
| 56 | JSON → DataFrame | [02 · mục 6](02%20JSON%20v%C3%A0%20Excel.md) |
| 57–62 | pd.read_json | [02 · mục 7](02%20JSON%20v%C3%A0%20Excel.md) |
| 64–67 | to_json, orient | [02 · mục 8](02%20JSON%20v%C3%A0%20Excel.md) |
| 69–71 | pd.read_html, bảng từ chuỗi HTML | [03 · mục 1](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| 72–78 | Bảng từ URL, Olympic, pie chart | [03 · mục 2](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| 80 | to_html | [03 · mục 3](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| 79, 81–86 | XML, RSS | [03 · mục 4](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| 87–89 | RSS → DataFrame, lọc tin | [03 · mục 5](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| 91–93 | Đọc Excel | [02 · mục 9](02%20JSON%20v%C3%A0%20Excel.md) |
| 94–96 | Ghi Excel, openpyxl, xlrd | [02 · mục 10–11](02%20JSON%20v%C3%A0%20Excel.md) |
| 98–102 | API web, requests | [03 · mục 6–8](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| 104–115 | sqlite3 | [03 · mục 9–10](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| 116–118 | SQLAlchemy | [03 · mục 11](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md), [Thực hành Excel nhiều sheet và SQLAlchemy](Th%E1%BB%B1c%20h%C3%A0nh%20Excel%20nhi%E1%BB%81u%20sheet%20v%C3%A0%20SQLAlchemy.md) |
| 119 | Bảng hàm đọc pandas | [04 · mục 1](04%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md) |
| 120 | Trang kết | không có nội dung thi |

## Sơ đồ

- [Chọn tham số read_csv](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Ch%E1%BB%8Dn%20tham%20s%E1%BB%91%20read_csv.excalidraw.md)
- [JSON qua lại Python và orient](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/JSON%20qua%20l%E1%BA%A1i%20Python%20v%C3%A0%20orient.excalidraw.md)
- [Theo dấu SQLite](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Theo%20d%E1%BA%A5u%20SQLite%20t%E1%BB%AB%20connect%20%C4%91%E1%BA%BFn%20close.excalidraw.md)
- [Chọn hàm đọc theo nguồn](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Ch%E1%BB%8Dn%20h%C3%A0m%20%C4%91%E1%BB%8Dc%20theo%20ngu%E1%BB%93n%20d%E1%BB%AF%20li%E1%BB%87u.excalidraw.md)
- [Quy trình chung](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Ch%C6%B0%C6%A1ng%204%20-%20Quy%20tr%C3%ACnh.excalidraw.md)

> **example** Xem sơ đồ quy trình chung
> [![Chương 4 - Quy trình](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Ch%C6%B0%C6%A1ng%204%20-%20Quy%20tr%C3%ACnh.excalidraw.svg)](../../diagrams/04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/Ch%C6%B0%C6%A1ng%204%20-%20Quy%20tr%C3%ACnh.excalidraw.md)

## Họ giải của chương

| Họ | Note lý thuyết |
| --- | --- |
| F401 read_csv | [01 CSV và schema](01%20CSV%20v%C3%A0%20schema.md) |
| F402 Ghi tệp | [Ghi CSV với to_csv](Ghi%20CSV%20v%E1%BB%9Bi%20to_csv.md) |
| F403 Excel | [02 JSON và Excel](02%20JSON%20v%C3%A0%20Excel.md) |
| F404 JSON | [02 JSON và Excel](02%20JSON%20v%C3%A0%20Excel.md) |
| F405 Web, XML, API | [03 Web API XML và SQLite](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| F406 SQLite | [03 Web API XML và SQLite](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |
| F407 Đường dẫn, tệp | [03 Web API XML và SQLite](03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) |

Tổng quan cụm: các họ bài của chương 4.

## Chuẩn đầu ra

- Đọc CSV có dấu phân cách khác mặc định và giữ được ID có số 0 đầu.
- Chọn đúng cách đọc JSON, Excel, HTML/XML, API hoặc SQLite theo nguồn.
- Biết kiểu trả về của từng hàm (DataFrame, list, dict, str, TextFileReader).
- Kiểm tra schema, shape và giá trị thiếu sau nạp.

## Liên hệ

Cần biết trước [NumPy và Pandas](../03%20NumPy%20v%C3%A0%20Pandas/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md). Dùng schema đã kiểm tra để sang [Làm sạch](../05%20L%C3%A0m%20s%E1%BA%A1ch/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md).

## Bài tình huống

CSV có id 001, số tiền dùng dấu phẩy thập phân và mã 'NA' hợp lệ trong cột mã vùng. Viết điều kiện đọc và kiểm tra.

> **check** Lập luận và ca biên
> Giữ ID dưới dạng chuỗi ngay từ lúc đọc (*`dtype={"id": str}`*). Khai báo *`sep`* và *`decimal=","`* nhất quán với dữ liệu. Đặt *`keep_default_na=False`* và chỉ cấu hình *`na_values`* theo cột có quy ước. Kiểm tra lại số hàng, dtype và khóa duy nhất sau đọc.
