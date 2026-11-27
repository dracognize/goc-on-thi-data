# Nhận diện cách thu nạp dữ liệu

**Quy tắc nhận diện và giải.** Phân loại tần suất xử lý trước, hướng chủ động gửi/lấy sau.

Cần biết trước [Kỹ thuật và phân tích dữ liệu](../../01%20T%E1%BB%95ng%20quan/02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md). Nguồn ScoreUp.

## 1. Cơ bản

Trường hợp nào sau đây phù hợp với xử lý streaming hơn là xử lý batch?

- **A.** Phát hiện giao dịch thẻ gian lận ngay lúc giao dịch đang phát sinh
- **B.** Lập báo cáo doanh thu tổng hợp vào cuối tháng cho phòng kế toán của công ty
- **C.** Tổng hợp thống kê nhân sự theo quý để gửi báo cáo lên cơ quan quản lý cấp trên
- **D.** Cập nhật bảng xếp hạng chi nhánh theo lịch chạy cố định vào lúc 2 giờ sáng mỗi ngày

> **tip** Gợi ý
> Xem trường hợp nào phải phản hồi ngay.

> **success** Đáp án và hướng giải
> **A.** Phát hiện gian lận khi giao dịch phát sinh cần luồng cập nhật liên tục. Chờ gom cuối ngày có thể bỏ lỡ thời điểm chặn.

Mã câu `Q00110` · Nhóm gốc 1.

## 2. Vận dụng

Một chuỗi cửa hàng cần (i) đối soát doanh thu toàn hệ thống vào 23 giờ mỗi đêm và (ii) cảnh báo ngay khi có giao dịch thẻ bất thường. Cơ chế thu nạp dữ liệu phù hợp tương ứng là gì?

- **A.** (i) batch; (ii) streaming
- **B.** Cả (i) và (ii) đều dùng batch
- **C.** (i) streaming; (ii) batch
- **D.** Cả (i) và (ii) đều dùng streaming

> **tip** Gợi ý
> Xác định thời điểm cần kết quả cho từng quy trình.

> **success** Đáp án và hướng giải
> **A.** Đối soát lúc 23 giờ gom theo lô. Cảnh báo ngay khi có giao dịch bất thường cần streaming.

Mã câu `Q00322` · Nhóm gốc 1.

## 3. Tổng hợp

Mỗi đêm lúc 1 giờ, hệ thống kế toán của một công ty tự gọi API ngân hàng để lấy sao kê trong ngày. Còn phần mềm bán hàng thì tự gửi từng đơn mới sang kho dữ liệu ngay khi khách thanh toán xong. Hai luồng thu nạp dữ liệu này được phân loại thế nào?

- **A.** Luồng sao kê là Push và xử lý theo lô; luồng đơn hàng là Pull và xử lý thời gian thực
- **B.** Luồng sao kê là Pull và xử lý theo lô; luồng đơn hàng là Push và xử lý thời gian thực
- **C.** Luồng sao kê là Pull và xử lý thời gian thực; luồng đơn hàng là Push và xử lý theo lô
- **D.** Luồng sao kê là Pull và xử lý theo lô; luồng đơn hàng cũng là Pull và xử lý thời gian thực

> **tip** Gợi ý
> Kiểm tra ai chủ động và khi nào dữ liệu đi, thành hai cột riêng.

> **success** Đáp án và hướng giải
> **B.** Sao kê do hệ thống kế toán tự gọi nên là pull và chạy một lần mỗi đêm nên batch. Bán hàng chủ động gửi từng sự kiện khi phát sinh nên push và thời gian thực.

Mã câu `Q00341` · Nhóm gốc 1.
