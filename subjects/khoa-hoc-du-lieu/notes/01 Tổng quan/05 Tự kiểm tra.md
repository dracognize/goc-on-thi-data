# Tự kiểm tra · Chương 01

Tự giải thích lý do trước khi mở đáp án. Mỗi câu tính một điểm khi trả lời đúng và nêu được lý do.

> **question** Làm nóng · Từ một hàng hóa đơn, chỉ ra quan sát, thuộc tính và khóa
> Nếu một hàng là một hóa đơn, quan sát là hóa đơn đó, thuộc tính có thể là ngày hoặc số tiền. Mã hóa đơn dùng làm khóa khi duy nhất. Mã khách có thể lặp giữa nhiều hóa đơn.

## Phần A · Khái niệm và chu trình

> **question** 1. Ba trụ cột của KHDL là gì?
> Toán học & thống kê; khoa học máy tính; kiến thức chuyên sâu về lĩnh vực (tr. 7).

> **question** 2. Sắp xếp: Đánh giá, Khai phá, Thu thập, Xây mô hình, Xác định bài toán, Triển khai, Xử lý.
> Xác định bài toán → Thu thập → Khai phá → Xử lý → Xây mô hình → Đánh giá → Triển khai & giám sát (tr. 10).

> **question** 3. Siêu thị ABC tạo biến "số ngày kể từ lần mua cuối". Bước nào?
> Bước 4 Xử lý, mục tạo đặc trưng (tr. 15).

> **question** 4. Vì sao KHDL trong kinh doanh ưa cây quyết định hơn mạng nơ-ron sâu?
> Cần giải thích "tại sao" cho nhà quản lý; cây quyết định là hộp trắng (tr. 22).

> **question** 5. Mô hình A accuracy 90%, lợi nhuận 100 triệu; B accuracy 88%, lợi nhuận 130 triệu. KHDL trong KT&KD chọn gì?
> B. Tiêu chí là lợi ích ròng (tr. 23).

## Phần B · Dữ liệu và kỹ thuật dữ liệu

> **question** 6. Tệp JSON thuộc loại cấu trúc nào? Email thì sao?
> Cả hai là bán cấu trúc (tr. 27).

> **question** 7. Chuẩn hóa mã tiền tệ trước khi nạp kho là ETL hay ELT?
> ETL. Transform đứng trước Load.

> **question** 8. Hệ thống đích chạy mỗi 24h để lấy dữ liệu từ API. Push hay pull? Batch hay streaming?
> Pull và batch (tr. 48).

> **question** 9. Thứ tự 5 bước kỹ thuật dữ liệu?
> Nguồn sinh → Lưu trữ → Thu nạp → Biến đổi → Phục vụ (tr. 38).

> **question** 10. Đưa phân khúc khách từ kho BI về CRM gọi là gì?
> Reverse ETL (tr. 56).

> **question** 11. Một đơn hàng bị đẩy lên hệ thống 2 lần vi phạm tiêu chí chất lượng nào?
> Duy nhất (uniqueness) (tr. 73).

## Phần C · Phân tích dữ liệu

> **question** 12. "Vì sao doanh thu chi nhánh B giảm?" thuộc cấp phân tích nào?
> Chẩn đoán.

> **question** 13. "Nên phân bổ ngân sách marketing thế nào để tối đa lợi nhuận?" thuộc cấp nào?
> Định hướng hành động (prescriptive).

> **question** 14. Metadata và nhật ký xử lý khác nhau thế nào?
> Metadata mô tả từng biến (đơn vị, nguồn, ý nghĩa, kiểu). Nhật ký ghi các bước xử lý, logic, giả định (tr. 74).

## Phần D · Học máy

> **question** 15. Dự đoán khách có mua gói dịch vụ bằng lịch sử đã biết kết quả là bài toán gì?
> Phân loại có giám sát.

> **question** 16. Vì sao Flyer bị loại khỏi mô hình quảng cáo?
> Hệ số 0.012 không có ý nghĩa thống kê (tr. 97).

> **question** 17. Ba bước của KNN?
> Tính khoảng cách tới mọi điểm huấn luyện; chọn k điểm gần nhất; gán nhãn đa số.

> **question** 18. R² = 0,47 nghĩa là gì?
> Mô hình giải thích khoảng 47% biến thiên của giá nhà.

> **question** 19. Chọn 2.000 khách theo mô hình được 484 người đồng ý. Tỷ lệ chuyển đổi?
> $484/2000 = 24{,}2\%$.

> **question** 20. Vì sao dùng số đơn trong tháng sau để dự đoán quay lại vào tháng sau là lỗi?
> Biến lấy từ khoảng thời gian cần dự đoán, chưa có ở thời điểm dự đoán (rò rỉ dữ liệu).

**Đạt** khi đúng ít nhất 16/20 và giải thích được câu đã đoán. Sai câu nào thì mở Thẻ nhớ chương 1 và họ bài tương ứng trong [Mục lục Chương 01](00%20M%E1%BB%A5c%20l%E1%BB%A5c.md).
