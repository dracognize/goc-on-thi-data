# Dự đoán bằng KNN

**Cần biết trước.** [Chương 08 - Hồi quy và KNN](../../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md).

**Quy trình giải.** Tính khoảng cách theo đặc trưng, lấy đúng k điểm gần nhất rồi đếm phiếu cho phân loại hoặc lấy trung bình mục tiêu cho hồi quy với trọng số đều.

Làm từng bài trước khi mở gợi ý, rồi so sánh quy tắc với bài trước.

## 1 · Cơ bản

Trong ví dụ KNN phân loại với K=3, khi dự đoán cho điểm 'Số giờ tự học = 4', ba hàng xóm gần nhất trong tập train là 4.5, 3 và 5.5 với nhãn lần lượt là Trượt, Trượt, Đạt. Mô hình sẽ dự đoán nhãn nào cho điểm này?

- **A.** Đạt, vì 5.5 gần điểm 4 nhất trong ba hàng xóm
- **B.** Không xác định được vì số phiếu 'Trượt' và 'Đạt' bằng nhau
- **C.** Đạt, vì trung bình cộng của ba hàng xóm lớn hơn 4
- **D.** Trượt, vì đa số hàng xóm (2/3) có nhãn Trượt

ID ScoreUp: `Q03573`

> **hint** Gợi ý 1
> Xác định khái niệm hoặc quy tắc được hỏi.

> **hint** Gợi ý 2
> Tính khoảng cách theo đặc trưng, lấy đúng k điểm gần nhất rồi đếm phiếu cho phân loại hoặc lấy trung bình mục tiêu cho hồi quy với trọng số đều.

> **check** Bài mẫu giải đầy đủ
> **D.** Ba nhãn có hai phiếu Trượt nên dự đoán Trượt.

## 2 · Vận dụng

Tập train gồm số nhân viên bán hàng (người): 1, 3, 4, 6, 8, 10 và doanh thu tương ứng (triệu VND): 12, 30, 33, 45, 60, 81. KNeighborsRegressor với K=3 dự đoán doanh thu cho cửa hàng có 7.5 nhân viên là bao nhiêu?

- **A.** 46 triệu
- **B.** 62 triệu
- **C.** 52.5 triệu
- **D.** 60 triệu

ID ScoreUp: `Q03554`

> **hint** Gợi ý 1
> Gạch dữ kiện có ảnh hưởng đến kết quả.

> **hint** Gợi ý 2
> Tính khoảng cách theo đặc trưng, lấy đúng k điểm gần nhất rồi đếm phiếu cho phân loại hoặc lấy trung bình mục tiêu cho hồi quy với trọng số đều.

> **check** Lời giải
> **B.** Ba điểm gần 7,5 nhất là 8, 6 và 10. Trung bình mục tiêu là (60 + 45 + 81)/3 = 62 triệu.

## 3 · Vận dụng mở rộng

Dùng KNeighborsRegressor với K=3 trên tập train của bài toán lương (kinh nghiệm: 1, 1.5, 2.5, 3, 4, 5, 5.5, 6 năm; lương tương ứng: 15, 18, 22, 25, 28, 35, 36, 40 triệu). Lương dự đoán cho người có 3.2 năm kinh nghiệm là bao nhiêu?

- **A.** 28.0 triệu
- **B.** 23.5 triệu
- **C.** 25.0 triệu
- **D.** 29.33 triệu

ID ScoreUp: `Q03567`

> **hint** Gợi ý 1
> Viết trạng thái trung gian hoặc xác định tác động của từng thao tác.

> **hint** Gợi ý 2
> Tính khoảng cách theo đặc trưng, lấy đúng k điểm gần nhất rồi đếm phiếu cho phân loại hoặc lấy trung bình mục tiêu cho hồi quy với trọng số đều.

> **check** Lời giải
> **C.** Ba điểm gần 3,2 nhất là 3, 2,5 và 4. Trung bình mục tiêu là (25 + 22 + 28)/3 = 25 triệu.
