# Phân phối và ngoại lệ

**Cần biết trước.** [Chương 07 - Chọn và đọc biểu đồ](../../07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md).

**Quy trình giải.** Xác định câu hỏi về hình dạng, độ phân tán hay ngoại lệ. Với boxplot, tính IQR trước rồi mới tính hai hàng rào. Với histogram so sánh hai nhóm rất lệch cỡ mẫu, thống nhất bin và chọn cách chuẩn hóa.

Làm từng bài trước khi mở gợi ý, rồi so sánh quy tắc với bài trước.

## 1 · Cơ bản

IQR (Interquartile Range) trong boxplot tính như thế nào?

- **A.** IQR = Q2 - Q1
- **B.** IQR = Giá trị lớn nhất - Giá trị nhỏ nhất
- **C.** IQR = Q3 - Q1
- **D.** IQR = (Q1 + Q3) / 2

ID ScoreUp: `Q03055`

> **hint** Gợi ý 1
> Xác định khái niệm hoặc quy tắc được hỏi.

> **hint** Gợi ý 2
> Xác định câu hỏi về hình dạng, độ phân tán hay ngoại lệ. Với boxplot, tính IQR trước rồi mới tính hai hàng rào. Với histogram so sánh hai nhóm rất lệch cỡ mẫu, thống nhất bin và chọn cách chuẩn hóa.

> **check** Bài mẫu giải đầy đủ
> **C.** IQR = Q3 − Q1.

## 2 · Vận dụng

Outlier trong boxplot thường được xác định như thế nào?

- **A.** Những giá trị nằm ngoài khoảng [Q1, Q3] của dữ liệu
- **B.** Những giá trị cách trung bình hơn 1.5 lần độ lệch chuẩn
- **C.** Những giá trị nằm ngoài khoảng [median - 1.5*IQR, median + 1.5*IQR]
- **D.** Những giá trị nằm ngoài khoảng [Q1 - 1.5*IQR, Q3 + 1.5*IQR]

ID ScoreUp: `Q03033`

> **hint** Gợi ý 1
> Gạch dữ kiện có ảnh hưởng đến kết quả.

> **hint** Gợi ý 2
> Xác định câu hỏi về hình dạng, độ phân tán hay ngoại lệ. Với boxplot, tính IQR trước rồi mới tính hai hàng rào. Với histogram so sánh hai nhóm rất lệch cỡ mẫu, thống nhất bin và chọn cách chuẩn hóa.

> **check** Lời giải
> **D.** Hàng rào thường đặt ở Q1 − 1,5 IQR và Q3 + 1,5 IQR.

## 3 · Vận dụng mở rộng

Cần so sánh hình dạng phân phối giá nhà giữa quận A (2000 căn) và quận B (200 căn). Hai histogram dạng đếm cho thấy cột quận A cao gấp nhiều lần, khó so sánh. Cách xử lý phù hợp nhất là gì?

- **A.** Tăng số bins của quận B cho đến khi chiều cao các cột của hai quận xấp xỉ bằng nhau rồi so sánh
- **B.** Chuẩn hóa mỗi nhóm về tỷ lệ hoặc mật độ (ví dụ density=True) để diện tích hai nhóm bằng nhau rồi so sánh
- **C.** So sánh trực tiếp chiều cao tuyệt đối của các cột vì đó là số căn nhà thực tế trong mỗi khoảng giá
- **D.** Chuyển sang biểu đồ cột cho từng quận vì histogram không phù hợp để so sánh hai nhóm với nhau

ID ScoreUp: `Q03104`

> **hint** Gợi ý 1
> Viết trạng thái trung gian hoặc xác định tác động của từng thao tác.

> **hint** Gợi ý 2
> Xác định câu hỏi về hình dạng, độ phân tán hay ngoại lệ. Với boxplot, tính IQR trước rồi mới tính hai hàng rào. Với histogram so sánh hai nhóm rất lệch cỡ mẫu, thống nhất bin và chọn cách chuẩn hóa.

> **check** Lời giải
> **B.** Số đếm thô chịu ảnh hưởng của cỡ mẫu. Cần đưa hai nhóm về thang tương đối và dùng cùng các khoảng chia.
