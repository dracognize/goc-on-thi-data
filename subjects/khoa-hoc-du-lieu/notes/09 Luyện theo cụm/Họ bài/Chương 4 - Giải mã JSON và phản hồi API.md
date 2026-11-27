# Giải mã JSON và phản hồi API

**Lý thuyết.** [JSON và Excel](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/02%20JSON%20v%C3%A0%20Excel.md) · [Bảng tra chương 4](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/04%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Xác định đầu vào là chuỗi JSON, phản hồi HTTP hay đối tượng Python. Sau giải mã, xác định danh sách bản ghi, hợp khóa và ô thiếu trước khi tính.

## Ví dụ có lời giải

Ví dụ mới: `json.loads('[{"id":1,"price":20},{"id":2}]')` trả danh sách hai dict. `pd.DataFrame(...)` tạo hai hàng và hai cột, có một ô thiếu ở `price`, còn `price.mean()` bằng 20.0.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Trong một tệp JSON có dòng {"ten": "Binh", "diem_anh": "null"} (chữ null được đặt trong nháy kép). Theo cấu trúc JSON, giá trị của diem_anh thuộc kiểu nào?

- **A.** Giá trị null
- **B.** Số (number) bằng 0
- **C.** Lỗi cú pháp, vì null không được đặt trong nháy kép
- **D.** Chuỗi (string) gồm 4 ký tự n, u, l, l

> **tip** Gợi ý
> Xem cặp dấu nháy quanh giá trị.

> **success** Đáp án D
> `"null"` là chuỗi bốn ký tự. JSON `null` không có nháy sẽ được giải mã thành `None` trong Python.

Nguồn ScoreUp, nhóm 4, ID `Q01496`.

### 2 · Vận dụng

Trong thư viện requests, response.text khác gì so với response.json()?

- **A.** response.text trả về dữ liệu đã chuyển thành dict Python, còn response.json() trả về chuỗi thô
- **B.** Cả hai đều trả về cùng một kiểu dict Python, response.json() là cách viết gọn hơn của response.text
- **C.** response.text trả về chuỗi văn bản thô, còn response.json() chuyển nội dung JSON thành dict/list Python
- **D.** response.text dùng cho phản hồi dạng XML, còn response.json() dùng cho phản hồi dạng HTML

> **tip** Gợi ý
> Tách việc đọc văn bản khỏi việc phân tích cú pháp.

> **success** Đáp án C
> `.text` trả chuỗi đã giải mã. `.json()` phân tích payload thành đối tượng Python, thường là dict/list với hai dạng payload trong bài.

Nguồn ScoreUp, nhóm 4, ID `Q01458`.

### 3 · Tổng hợp

Dữ liệu từ API là danh sách dict, trong đó một bản ghi thiếu khóa gia. Dòng in ra cho kết quả nào?

```python
import pandas as pd

data = [
    {"san_pham": "Áo thun", "gia": 100, "kho": "HN"},
    {"san_pham": "Quần jean", "gia": 200, "kho": "HCM"},
    {"san_pham": "Mũ lưỡi trai", "kho": "HN"},
]
df = pd.DataFrame(data)
print(df.shape, df["gia"].isna().sum(), df["gia"].mean())
```

- **A.** (3, 3) 1 NaN
- **B.** (3, 3) 1 150.0
- **C.** (3, 3) 1 100.0
- **D.** (2, 3) 0 150.0

> **tip** Gợi ý
> Một dict thiếu khóa có làm mất toàn bộ bản ghi không?

> **success** Đáp án B
> Có ba bản ghi và ba khóa hợp, tạo shape `(3, 3)`. Thiếu `gia` ở một hàng. Trung bình hai giá trị 100 và 200 bằng 150.0.

Nguồn ScoreUp, nhóm 4, ID `Q01476`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
