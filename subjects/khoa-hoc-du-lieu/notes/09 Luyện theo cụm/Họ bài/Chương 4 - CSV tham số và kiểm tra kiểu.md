# CSV tham số và kiểm tra kiểu

**Lý thuyết.** [CSV và schema](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/01%20CSV%20v%C3%A0%20schema.md) · [Bảng tra chương 4](../../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/04%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Tách dấu phân trường, dấu thập phân và dấu hiệu thiếu. Sau đó xác định tên cột, kiểu dữ liệu và số ô thiếu trước khi tính thống kê.

## Ví dụ có lời giải

Ví dụ mới: tệp có tiêu đề `id;gia` và dòng `001;2,5`. Chọn `sep=';'`, `decimal=','`, `dtype={'id':'string'}`. Bảng có shape `(1, 2)`, ID `001` và giá 2.5. Nếu quên `decimal`, cột giá có thể được đọc như chuỗi.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Nếu không truyền tham số sep, hàm pd.read_csv dùng ký tự nào làm dấu phân tách giữa các cột?

- **A.** Ký tự tab
- **B.** Dấu phẩy (,)
- **C.** Dấu chấm phẩy (;)
- **D.** Một hoặc nhiều khoảng trắng

> **tip** Gợi ý
> Nhớ định dạng mà CSV viết tắt.

> **success** Đáp án B
> `read_csv` mặc định dùng dấu phẩy. Với dữ liệu phân tách khác, truyền `sep` tường minh.

Nguồn ScoreUp, nhóm 4, ID `Q01482`.

### 2 · Vận dụng

Tệp điểm nạp từ chuỗi có dòng Binh,80 thiếu trường cuối cùng (cột Van). Lệnh print in ra điểm trung bình cột Van và số ô thiếu của cột đó. Kết quả là gì?

```python
import pandas as pd
from io import StringIO

text = """Ma,Toan,Van
An,90,60
Binh,80
Chi,70,90"""
df = pd.read_csv(StringIO(text))
print(df["Van"].mean(), df["Van"].isnull().sum())
```

- **A.** 50.0 1
- **B.** 75.0 1
- **C.** nan 1
- **D.** 75.0 0

> **tip** Gợi ý
> Viết riêng ba giá trị ở cột Van sau khi nạp.

> **success** Đáp án B
> Van là 60, thiếu, 90. `mean()` bỏ ô thiếu theo mặc định nên được 75.0. `isnull().sum()` đếm một ô.

Nguồn ScoreUp, nhóm 4, ID `Q01457`.

### 3 · Tổng hợp

Tệp CSV dùng dấu chấm phẩy làm dấu phân tách và dấu phẩy làm dấu thập phân (kiểu Việt Nam). Đoạn code sau in ra gì?

```python
import pandas as pd
import io

s = "san_pham;gia\nCa phe;45,5\nTra;30,25\n"
d = pd.read_csv(io.StringIO(s), sep=";", decimal=",")
print(d["gia"].sum(), d["gia"].dtype)
```

- **A.** 75.75 float64
- **B.** 45,530,25 object
- **C.** 7575 int64
- **D.** ValueError

> **tip** Gợi ý
> Tách bước nhận diện trường khỏi bước nhận diện số.

> **success** Đáp án A
> Dấu chấm phẩy tạo cột `gia`. Dấu phẩy được phân tích thành phần thập phân, nên 45.5 + 30.25 = 75.75 và kiểu `float64` trong ví dụ.

Nguồn ScoreUp, nhóm 4, ID `Q01498`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
