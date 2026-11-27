# Tự kiểm tra · Chương 07

> **question** Bạn có doanh thu từng tháng của ba kênh. Muốn xem thời điểm ba kênh tăng giảm thì chọn gì?
> Dùng đường theo tháng đã sắp thứ tự, một đường mỗi kênh. Nếu quá nhiều kênh khó đọc, thử small multiples cùng thang đo.

> **question** Nhóm A có 2 dòng với giá trị 4 và 8. Nhóm B có một dòng với giá trị 10. Đếm dòng và so trung bình khác thế nào?
> Countplot cho A=2 và B=1. Barplot theo trung bình cho A=6 và B=10. Nếu cần tổng, kết quả là A=12 và B=10.

> **question** Tỷ trọng từng kênh trong một tháng dùng mẫu số nào?
> Dùng tổng các kênh thuộc đúng tháng đó. Kiểm tra hàng chuẩn hóa có tổng 1 khi tổng gốc dương.

> **question** Ba subplot vẽ chung một figure. Bạn muốn xuất cả ba thì gọi ở đâu?
> Gọi **`fig.savefig(...)`** trên Figure đang chứa cả ba Axes.

> **question** Mã kênh 1, 2, 3 và số đơn 14, 8, 10. Cột nào nên đọc như biến số?
> Số đơn là biến định lượng. Mã kênh chỉ định danh, nên hiển thị như danh mục dù được lưu dạng số.

> **question** Với x = [1, 3], y = [8, 5], một scatter có những chấm nào?
> Hai chấm là (1, 8) và (3, 5). Các phần tử ở cùng vị trí trong hai danh sách tạo một cặp.

> **question** Vì sao dùng line qua Tháng 1 và Tháng 3 có thể làm người xem hiểu quá mức?
> Đoạn nối có thể tạo cảm giác đã biết chuyển động của tháng 2. Ghi rõ thiếu dữ liệu hoặc đặt một điểm thiếu để đường không chạy qua tháng đó.

**Bài làm.** Tạo bảng gồm tháng, kênh và số đơn. Vẽ xu hướng, tỷ trọng và phân phối trên ba hình. Viết một kết luận cùng một yếu tố có thể làm người xem hiểu sai cho từng hình.

## Bộ câu bổ sung theo slide

> **question** (7.1) Ai khởi xướng matplotlib và năm nào? Lấy cảm hứng từ phần mềm nào?
> John Hunter, 2002, giao diện vẽ giống MATLAB. [Xem 7.1.1](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md)

> **question** (7.1) Ba nguyên tắc cơ bản của trực quan hóa?
> Rõ ràng, trung thực, có mục tiêu. [Xem 7.1.3](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md)

> **question** (7.1) Dữ liệu lãi/lỗ quanh 0 nên dùng bảng màu nào?
> Diverging (đối xứng, ví dụ xanh – trắng – đỏ).

> **question** (7.2) Biểu đồ nào kết hợp boxplot với mật độ?
> Violin plot.

> **question** (7.2) Dữ liệu `1, 3, 5, 7, 9, 11, 40` có $Q_1 = 4$, $Q_3 = 10$. Râu trên dừng ở đâu?
> $IQR = 6$, hàng rào trên $= 19$. 40 là ngoại lai. Râu trên dừng ở 11.

> **question** (7.3) `fig.add_subplot(2, 2, 3)` tương ứng `axes[?, ?]`?
> `axes[1, 0]` (hàng 2, cột 1).

> **question** (7.3) `plt.plot(t, t**2, 'bs')` vẽ gì?
> Marker vuông xanh lam, không nối đường.

> **question** (7.3) Legend `loc=4` ở đâu?
> Dưới phải (`'lower right'`).

> **question** (7.3) Lưu PNG 300 dpi cắt sát lề?
> **`fig.savefig("h.png", dpi=300, bbox_inches="tight")`**.

> **question** (7.3) Khôi phục mọi cấu hình matplotlib về mặc định?
> **`mpl.rcdefaults()`** (hoặc **`plt.rcdefaults()`**).

> **question** (7.4) `df.plot()` tương đương phương thức nào?
> **`df.plot.line()`**.

> **question** (7.4) `sns.catplot(..., hue="time", col="smoker")` khác `row="time", col="smoker"` thế nào?
> Lệnh đầu: 2 ô, time tô màu trong mỗi ô. Lệnh sau: lưới 2×2, time tách thành hàng.

Ôn thêm bằng Thẻ nhớ chương 7.
