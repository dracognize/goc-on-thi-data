# Đọc nhiều bảng HTML

**Lý thuyết.** [Web API XML và SQLite](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) · [Bảng tra chương 4](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/04%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** `read_html` trả danh sách. Xác định bảng cần dựa trên thứ tự, văn bản hoặc schema, rồi kiểm tra bảng trước khi lưu.

## Ví dụ có lời giải

Ví dụ mới: trang có ba bảng, chỉ bảng thứ ba có chữ Doanh thu. `pd.read_html(url, match='Doanh thu')` trả danh sách có một phần tử nếu chỉ một bảng khớp. Lấy phần tử `[0]`, kiểm tra schema và giá trị thiếu rồi xuất.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Khi read_html() có nhiều bảng trong một trang, làm thế nào để lấy bảng thứ 2?

- **A.** pd.read_html(url, index=1)
- **B.** pd.read_html(url)[2]
- **C.** pd.read_html(url, match='table')[0]
- **D.** pd.read_html(url)[1]

> **tip** Gợi ý
> Đếm vị trí danh sách từ 0.

> **success** Đáp án D
> Bảng thứ hai là phần tử `[1]` của danh sách DataFrame.

Nguồn ScoreUp, nhóm 4, ID `Q01471`.

### 2 · Vận dụng

Một trang web có 5 bảng, trong đó chỉ một bảng có chứa chữ Closing Date. Lệnh pd.read_html(url, match='Closing Date') cho kết quả nào?

- **A.** Ngoại lệ TypeError vì match chỉ nhận số thứ tự của bảng cần đọc
- **B.** Danh sách đủ 5 bảng, trong đó mỗi bảng chỉ giữ lại cột Closing Date
- **C.** Một DataFrame duy nhất gồm những dòng có chứa chữ Closing Date
- **D.** Một danh sách chỉ gồm các bảng có văn bản khớp, ở đây là một DataFrame

> **tip** Gợi ý
> `match` kiểm tra văn bản trong bảng, hãy giữ rõ kiểu trả về.

> **success** Đáp án D
> Danh sách kết quả gồm một DataFrame. Tham số `match` chọn bảng có nội dung khớp.

Nguồn ScoreUp, nhóm 4, ID `Q01475`.

### 3 · Tổng hợp

Cho các bước: (a) tables = pd.read_html(url); (b) failures = tables[0]; (c) failures.isnull().sum() để kiểm tra dữ liệu thiếu; (d) failures.to_csv('bank_failures.csv', index=False). Thứ tự hợp lý để lấy bảng từ web, kiểm tra rồi lưu lại là gì?

- **A.** (a) → (b) → (c) → (d)
- **B.** (b) → (a) → (c) → (d)
- **C.** (a) → (c) → (b) → (d)
- **D.** (d) → (a) → (b) → (c)

> **tip** Gợi ý
> `isnull().sum()` ở đây cần đầu vào là DataFrame.

> **success** Đáp án A
> Đọc danh sách → lấy bảng → kiểm tra thiếu → ghi CSV. Chạy kiểm tra sau khi đã chọn bảng `failures`.

Nguồn ScoreUp, nhóm 4, ID `Q01477`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
