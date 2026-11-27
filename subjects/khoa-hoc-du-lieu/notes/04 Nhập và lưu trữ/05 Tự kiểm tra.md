# Tự kiểm tra · Chương 4

> **question** Làm nóng · Tệp bắt đầu bằng cột id và diem, sau đó có dòng 001;8. Vì sao đọc mặc định dễ sai hai lần?
> Dấu chấm phẩy cần *`sep=";"`*. Sau khi tách được cột, bộ đọc có thể suy id thành số, làm mất hai số 0. Chỉ định *`dtype={"id":"string"}`* rồi so với dữ liệu nguồn.

Đóng slide, viết đáp án và lý do trước khi mở từng thẻ. Ghi lại câu sai hoặc trả lời do đoán để kiểm tra sau 1, 3 và 7 ngày.

> **question** 1. Tệp không có tiêu đề, cần giữ id 001. Chọn hai tùy chọn nào?
> *`header=None`* (có thể kèm *`names`*) và *`dtype={'id':'string'}`* nếu đã đặt tên id.

> **question** 2. API trả 200 nhưng payload là HTML. `response.json()` cho kết quả gì?
> Có thể ném lỗi giải mã JSON. Mã trạng thái 200 cho biết phản hồi HTTP thành công, chưa xác nhận payload là JSON.

> **question** 3. Đọc tất cả sheet Excel được đối tượng gì?
> Một dict ánh xạ tên sheet sang DataFrame khi đặt *`sheet_name=None`*.

> **question** 4. Tại sao nên đọc lại CSV sau khi xuất?
> Để kiểm tra round-trip cho schema cần giữ. CSV không lưu đầy đủ dtype, do đó có thể phải truyền lại dtype khi đọc.

## Bộ câu theo slide (trắc nghiệm nhanh)

> **question** 5. CSV là tệp gì? (A) nhị phân nén (B) văn bản thuần (C) chỉ chứa số
> **B.** Văn bản thuần, mỗi dòng một bản ghi (tr. 8).

> **question** 6. `pd.read_csv("ex2.csv")` khi tệp không có tiêu đề gây lỗi gì?
> Dòng dữ liệu đầu thành tên cột, mất một bản ghi. Sửa: *`header=None`* hoặc *`names=[...]`* (tr. 16).

> **question** 7. `index_col=["key1","key2"]` tạo gì?
> Chỉ số phân cấp (MultiIndex) hai mức (tr. 19).

> **question** 8. Tệp tách bằng nhiều khoảng trắng không đều dùng `sep` nào?
> *`sep=r"\s+"`* (tr. 23).

> **question** 9. Có `na_values=vals` (dict) và `keep_default_na=False`. Ô rỗng ở cột không có trong dict thành gì?
> Chuỗi rỗng `''`, không phải NaN (tr. 28).

> **question** 10. `pd.read_csv(p, chunksize=1000)` trả kiểu gì?
> `TextFileReader`, lặp được và có **`get_chunk`** (tr. 31).

> **question** 11. `data.to_csv(sys.stdout, index=False, header=False)` in ra dòng đầu nào với bảng something/a/b/c/d/message?
> `one,1,2,3.0,4,` (tr. 39).

> **question** 12. JSON `null`, `true` chuyển sang Python thành gì?
> `None`, `True` (tr. 49).

> **question** 13. `json.dumps({"ten": "Bình"})` cho chuỗi gì?
> `{"ten": "B\u00ecnh"}` vì *`ensure_ascii=True`* mặc định (tr. 53).

> **question** 14. `to_json(orient="values")` trên bảng 2×2 cho gì?
> `[[1,2],[3,4]]` — chỉ giá trị (tr. 66).

> **question** 15. `pd.read_html` trả kiểu gì?
> List các DataFrame (tr. 69).

> **question** 16. Trong RSS, mỗi bài viết nằm trong thẻ nào?
> `<item>` bên trong `<channel>` (tr. 85).

> **question** 17. Đọc nhiều sheet trong một tệp, cách nào nhanh hơn?
> Tạo **`pd.ExcelFile`** một lần rồi **`.parse`** (tr. 93).

> **question** 18. Sau `con.executemany(...)` cần gọi gì để lưu?
> **`con.commit()`** (tr. 111).

> **question** 19. Lỗi nào được bắt khi `CREATE TABLE` một bảng đã tồn tại?
> **`sqlite3.OperationalError`** (tr. 109).

> **question** 20. Hàm nào đọc dữ liệu có độ rộng cột cố định?
> **`pd.read_fwf`** (tr. 119).

Ôn lặp lại bằng Thẻ nhớ chương 4.

Sau lượt đầu, thay dữ kiện trong một câu và giải lại từ đầu. Ôn quy tắc trong [04 Công thức và cú pháp](04%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md).

[Mục lục chương 4](00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
