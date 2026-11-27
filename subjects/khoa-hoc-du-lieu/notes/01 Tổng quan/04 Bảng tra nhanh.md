# Bảng tra nhanh · Chương 01

Dùng bảng khi tự hỏi “dữ liệu đến từ đâu, cần làm gì, kết quả cho ai?”. Ví dụ máy bán hàng gửi lẻ từng đơn nhưng nhân viên chỉ tổng hợp cuối ca. Nguồn chủ động gửi là push, còn việc gộp số cuối ca là batch. Hai từ trả lời hai câu hỏi khác nhau.

## Dấu hiệu trong đề → đáp án

| Dấu hiệu | Đáp án | Trang |
| --- | --- | --- |
| Làm rõ mục tiêu, KPI, yêu cầu dữ liệu | Bước 1 Xác định bài toán | tr. 10 |
| Vẽ biểu đồ, thống kê mô tả, hình thành giả thuyết | Bước 3 Khai phá | tr. 10 |
| Xử lý thiếu, mã hóa biến phân loại, tạo đặc trưng | Bước 4 Xử lý | tr. 10 |
| Chọn thuật toán, chia train/test, tối ưu tham số | Bước 5 Xây mô hình | tr. 10 |
| Huấn luyện lại khi hành vi khách thay đổi | Bước 7 Triển khai & giám sát | tr. 18 |
| Cần giải thích cho nhà quản lý | Mô hình hộp trắng: cây quyết định, logistic | tr. 22 |
| Đánh giá theo tiền tiết kiệm/tăng thêm | Chi phí – lợi ích (KT&KD) | tr. 23 |
| Bước 1–2 / 3–4 / 5–7 | KT dữ liệu / Phân tích / Học máy | tr. 25 |
| Email, JSON, XML | Bán cấu trúc | tr. 27 |
| Ảnh, video, bài đăng | Phi cấu trúc | tr. 27 |
| Website không có API | Web scraping | tr. 30 |
| Kafka, Spark, Storm | Streaming | tr. 30 |
| ggplot2, dplyr, Shiny | R | tr. 31 |
| "Đường ống và kho chứa" | Data Engineer | tr. 32 |
| "Kể chuyện bằng dữ liệu" | Data Analyst | tr. 32 |
| "Biến mô hình thành sản phẩm" | ML Engineer | tr. 32 |
| 70–80% thời gian dự án | Chuẩn bị và xử lý dữ liệu | tr. 36 |
| Thứ tự KT dữ liệu | Nguồn → Lưu trữ → Thu nạp → Biến đổi → Phục vụ | tr. 38 |
| Kho thô, mọi định dạng | Data Lake | tr. 43 |
| Kho theo phòng ban | Data Mart | tr. 43 |
| Dữ liệu nóng / nguội | Yếu tố tần suất truy cập | tr. 44 |
| Xử lý vào giờ cố định | Batch | tr. 47 |
| Liên tục, thời gian thực | Streaming | tr. 47 |
| Nguồn chủ động gửi | Push | tr. 48 |
| Đích lấy theo lịch | Pull | tr. 48 |
| Biến đổi trước khi nạp | ETL | tr. 49 |
| Nạp xong mới biến đổi | ELT | tr. 49 |
| Kho → CRM | Reverse ETL | tr. 54 |
| Cảnh báo tồn kho gần thời gian thực | Operational Analytics | tr. 56 |
| Câu hỏi "đã/tại sao" | Phân tích dữ liệu | tr. 61 |
| GDP của Tổng cục Thống kê | Nguồn thứ cấp | tr. 67 |
| Merge, pivot | Tái cấu trúc | tr. 72 |
| Mô tả đơn vị, nguồn, kiểu từng biến | Metadata | tr. 74 |
| ANOVA, kiểm định | Chẩn đoán | tr. 78 |
| Tối ưu ngân sách, lộ trình | Định hướng hành động | tr. 80 |
| Nhãn số liên tục | Hồi quy | tr. 95 |
| Nhãn lớp (kể cả mã 0/1/2) | Phân loại | tr. 100 |
| Không nhãn, tìm nhóm | Không giám sát | tr. 89 |
| Thưởng/phạt từ môi trường | Học tăng cường | tr. 89 |
| MAE, MSE, R² | Đánh giá hồi quy | tr. 113 |

## Số cần nhớ

[![C1 04 Bảng tra nhanh – bảng 1](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%2004%20B%E1%BA%A3ng%20tra%20nhanh%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/01%20T%E1%BB%95ng%20quan/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C1%2004%20B%E1%BA%A3ng%20tra%20nhanh%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Số | Ý nghĩa |
> | --- | --- |
> | 3 / 7 / 3 | Trụ cột / bước chu trình / lĩnh vực chuyên sâu |
> | 5 / 4 / 4 | Bước KT dữ liệu / bước phân tích / cấp độ phân tích |
> | 70–80% | Thời gian chuẩn bị dữ liệu |
> | 55 cửa hàng | Ca quảng cáo |
> | 150 hoa, 49/50 = 98% | Ca Iris |
> | MAE ≈ 27,88; R² ≈ 0,46–0,47 | Ca giá nhà |
> | 2.000/20.000; 9,3%; 186 → 484 (24,2%) | Ca ngân hàng |

Chi tiết ở [Mục lục chương 1](00%20M%E1%BB%A5c%20l%E1%BB%A5c.md).
