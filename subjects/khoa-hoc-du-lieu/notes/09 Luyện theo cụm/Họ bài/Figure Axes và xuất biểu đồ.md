# Figure Axes và xuất biểu đồ

**Cần biết trước.** [Chương 07 - Figure Axes và dữ liệu vẽ](../../07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md).

**Quy trình giải.** Xác định thao tác thuộc Figure hay một Axes. Tách ba việc tạo đối tượng, chỉnh bố cục, lưu hình.

Làm từng bài trước khi mở gợi ý, rồi so sánh quy tắc với bài trước.

## 1 · Cơ bản

Gọi fig, ax = plt.subplots() không truyền tham số nào. Giá trị nhận được là gì?

- **A.** fig là Figure còn ax là mảng numpy 1x1 chứa các Axes
- **B.** Chỉ một đối tượng Axes, không có Figure
- **C.** fig là Figure và ax là danh sách gồm 2 Axes cho trục x và trục y
- **D.** fig là Figure và ax là một đối tượng Axes đơn lẻ

ID ScoreUp: `Q03076`

> **hint** Gợi ý 1
> Xác định khái niệm hoặc quy tắc được hỏi.

> **hint** Gợi ý 2
> Xác định thao tác thuộc Figure hay một Axes. Tách ba việc tạo đối tượng, chỉnh bố cục, lưu hình.

> **check** Bài mẫu giải đầy đủ
> **D.** Không tham số, subplots tạo một Figure và một Axes.

## 2 · Vận dụng

Khi lưu biểu đồ bằng phương thức savefig() trong thư viện Matplotlib, tham số dpi (dots per inch) có vai trò điều chỉnh yếu tố nào của file ảnh đầu ra?

- **A.** Màu sắc của ảnh.
- **B.** Độ phân giải của ảnh xuất ra.
- **C.** Định dạng file lưu trữ.
- **D.** Số lượng đồ thị con trong ảnh.

ID ScoreUp: `Q03021`

> **hint** Gợi ý 1
> Gạch dữ kiện có ảnh hưởng đến kết quả.

> **hint** Gợi ý 2
> Xác định thao tác thuộc Figure hay một Axes. Tách ba việc tạo đối tượng, chỉnh bố cục, lưu hình.

> **check** Lời giải
> **B.** DPI là mật độ điểm ảnh khi kết xuất ảnh raster. Trong cùng kích thước inch, DPI cao hơn cho nhiều pixel hơn.

## 3 · Vận dụng mở rộng

Bạn dựng dashboard lưới 2x2 bằng plt.subplots(2, 2) nhưng tiêu đề và nhãn trục của các biểu đồ con bị đè lên nhau. Lệnh nào khắc phục trực tiếp vấn đề bố cục này?

- **A.** plt.legend(loc="best")
- **B.** plt.savefig("hinh.png")
- **C.** fig.tight_layout(pad=1.0)
- **D.** plt.close("all")

ID ScoreUp: `Q03072`

> **hint** Gợi ý 1
> Viết trạng thái trung gian hoặc xác định tác động của từng thao tác.

> **hint** Gợi ý 2
> Xác định thao tác thuộc Figure hay một Axes. Tách ba việc tạo đối tượng, chỉnh bố cục, lưu hình.

> **check** Lời giải
> **C.** Các tiêu đề và nhãn đè lên nhau là vấn đề bố cục. Dùng cơ chế tự điều chỉnh khoảng cách theo nội dung.
