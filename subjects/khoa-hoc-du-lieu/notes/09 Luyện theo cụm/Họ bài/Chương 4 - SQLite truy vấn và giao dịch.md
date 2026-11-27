# SQLite truy vấn và giao dịch

**Lý thuyết.** [Web API XML và SQLite](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/03%20Web%20API%20XML%20v%C3%A0%20SQLite.md) · [Bảng tra chương 4](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/04%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Phân biệt kết nối, giao dịch và bản sao kết quả truy vấn. Theo dõi chính xác lệnh nào commit trước khi đóng kết nối.

## Ví dụ có lời giải

Ví dụ mới: sau khi tạo và commit bảng, chèn dòng 1 và commit, sau đó chèn dòng 2 rồi rollback. `SELECT COUNT(*)` cho 1. Sửa ô trong DataFrame tra cứu cũng không thay đổi kết quả SQL.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Khi gọi con = sqlite3.connect("mydata.sqlite") mà tệp mydata.sqlite chưa tồn tại trên đĩa, điều gì sẽ xảy ra?

- **A.** Chương trình sẽ báo lỗi FileNotFoundError và dừng lại ngay
- **B.** Kết nối sẽ được tạo tạm trong RAM, không có tệp nào được ghi ra đĩa
- **C.** sqlite3 sẽ tự tìm một tệp .sqlite bất kỳ khác trong thư mục hiện tại để kết nối thay thế
- **D.** Python sẽ tự động tạo mới tệp mydata.sqlite rồi kết nối tới tệp đó

> **tip** Gợi ý
> Giả sử đường dẫn có thư mục cha hợp lệ và quyền ghi.

> **success** Đáp án D
> `connect` tới đường dẫn SQLite thông thường có thể tạo tệp mới nếu chưa tồn tại.

Nguồn ScoreUp, nhóm 4, ID `Q01465`.

### 2 · Vận dụng

Sau khi tạo DataFrame df từ kết quả SELECT * FROM test, sinh viên chạy df.loc[0, "d"] = 99 rồi truy vấn lại bảng test bằng cùng kết nối. Giá trị cột d của dòng đầu khi truy vấn lại là gì?

- **A.** Thành 99, vì DataFrame tự đồng bộ với bảng của kết nối đang mở
- **B.** Vẫn là giá trị cũ, vì df là bản sao trong bộ nhớ, không nối với bảng
- **C.** Thành 99 sau khi gọi con.commit(), vì commit ghi các thay đổi của DataFrame
- **D.** Báo lỗi vì không được sửa DataFrame được tạo từ một truy vấn SQL

> **tip** Gợi ý
> DataFrame có gắn đồng bộ với bảng SQL không?

> **success** Đáp án B
> Giá trị gốc giữ nguyên trong SQL. Gán vào `df.loc` chỉ sửa dữ liệu trong Python.

Nguồn ScoreUp, nhóm 4, ID `Q01466`.

### 3 · Tổng hợp

Đoạn code chèn hai lô dữ liệu, chỉ commit lô đầu rồi đóng kết nối, sau đó mở lại tệp để đọc. Kết quả nào đúng?

```python
import sqlite3

con = sqlite3.connect("ban.sqlite")
con.execute("CREATE TABLE ct (ma INTEGER, tien REAL)")
con.commit()
con.executemany("INSERT INTO ct VALUES(?, ?)", [(1, 2.5), (2, 4.0)])
con.commit()
con.executemany("INSERT INTO ct VALUES(?, ?)", [(3, 1.5), (4, 0.5)])
con.close()

con = sqlite3.connect("ban.sqlite")
rows = con.execute("SELECT * FROM ct").fetchall()
print(len(rows), sum(r[1] for r in rows))
con.close()
```

- **A.** In ra 2 6.5, vì lô chưa commit bị bỏ khi đóng kết nối
- **B.** In ra 4 8.5, vì close() tự lưu cả lô chưa commit vào tệp
- **C.** In ra 0 0, vì không có dòng nào được ghi xuống tệp
- **D.** Báo lỗi, vì không được connect lại sau khi đã close

> **tip** Gợi ý
> Vẽ mốc commit sau mỗi lô và cộng giá trị các dòng đã lưu.

> **success** Đáp án A
> Lô 1 được commit. Trong ngữ cảnh mặc định của bài, lô 2 chưa commit bị bỏ khi đóng. Truy vấn cho 2 dòng và tổng 6.5, với giả định tệp mới.

Nguồn ScoreUp, nhóm 4, ID `Q01464`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
