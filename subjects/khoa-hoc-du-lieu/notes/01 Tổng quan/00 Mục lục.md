# Chương 01 · Tổng quan khoa học dữ liệu

**Bắt đầu từ số 0.** Dữ liệu là điều được ghi lại, như mỗi hóa đơn có ngày, mã khách và số tiền. Một hàng thường là một quan sát, một cột mô tả một thuộc tính. Chương này đi từ khái niệm KHDL → hạ tầng dữ liệu → phân tích → học máy, dùng chung ví dụ hóa đơn và bốn ca thực tế.

## Thứ tự đọc

1. [01 Chu trình khoa học dữ liệu](01%20Chu%20tr%C3%ACnh%20khoa%20h%E1%BB%8Dc%20d%E1%BB%AF%20li%E1%BB%87u.md): 3 trụ cột, 7 bước, đặc thù kinh doanh, 3 lĩnh vực.
2. [06 Dữ liệu và vị trí công việc](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md): loại dữ liệu, định dạng, nguồn, ngôn ngữ, 4 vị trí.
3. [02 Kỹ thuật dữ liệu](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md): 5 bước, batch/stream, push/pull, ETL/ELT, phục vụ.
4. [07 Quy trình phân tích dữ liệu](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md): 4 bước, 4 cấp độ, storytelling.
5. [03 Nhãn và loại bài toán](03%20Nh%C3%A3n%20v%C3%A0%20lo%E1%BA%A1i%20b%C3%A0i%20to%C3%A1n.md): học máy, 3 loại, chọn hồi quy/phân loại.
6. [Bốn ca học máy trong lecture](B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture.md): quảng cáo, Iris, giá nhà, ngân hàng.
7. Tra [04 Bảng tra nhanh](04%20B%E1%BA%A3ng%20tra%20nhanh.md) → làm [05 Tự kiểm tra](05%20T%E1%BB%B1%20ki%E1%BB%83m%20tra.md) → ôn Thẻ nhớ chương 1 (thẻ `flashcards/chuong-1`).

**Đầu ra.** Viết được 7 bước cho một bài toán kinh doanh; xếp đúng 5 bước kỹ thuật dữ liệu; phân biệt batch/streaming, push/pull, ETL/ELT; gọi tên cấp độ phân tích từ câu hỏi; xác định loại học máy và chỉ số đánh giá.

## Bản đồ chương



## Sơ đồ Excalidraw

| Sơ đồ | Trả lời câu hỏi |
| --- | --- |
| [Bảy bước chu trình](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20B%E1%BA%A3y%20b%C6%B0%E1%BB%9Bc%20chu%20tr%C3%ACnh%20v%C3%A0%20%C4%91%E1%BA%A7u%20ra.excalidraw.md) | Bước nào cho ra đầu ra nào, lĩnh vực nào phụ trách? |
| [Năm bước kỹ thuật dữ liệu](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20N%C4%83m%20b%C6%B0%E1%BB%9Bc%20k%E1%BB%B9%20thu%E1%BA%ADt%20d%E1%BB%AF%20li%E1%BB%87u.excalidraw.md) | Thứ tự và công cụ của từng bước? |
| [ETL và ELT](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20ETL%20v%C3%A0%20ELT.excalidraw.md) | Biến đổi trước hay sau khi nạp? |
| [Bốn cấp độ phân tích](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20B%E1%BB%91n%20c%E1%BA%A5p%20%C4%91%E1%BB%99%20ph%C3%A2n%20t%C3%ADch.excalidraw.md) | Câu hỏi nào thuộc cấp độ nào? |
| [Chọn loại bài toán](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20Ch%E1%BB%8Dn%20lo%E1%BA%A1i%20b%C3%A0i%20to%C3%A1n%20h%E1%BB%8Dc%20m%C3%A1y.excalidraw.md) | Giám sát, không giám sát hay tăng cường? |
| [KNN bỏ phiếu](../../diagrams/01%20T%E1%BB%95ng%20quan/C1%20KNN%20b%E1%BB%8F%20phi%E1%BA%BFu.excalidraw.md) | KNN gán nhãn ra sao? |
| [Từ câu hỏi đến hành động](../../diagrams/01%20T%E1%BB%95ng%20quan/T%E1%BB%AB%20c%C3%A2u%20h%E1%BB%8Fi%20%C4%91%E1%BA%BFn%20h%C3%A0nh%20%C4%91%E1%BB%99ng.excalidraw.md) | Sơ đồ cũ: từ bài toán đến giám sát |

## Phủ slide

| Trang | Chủ đề | Note |
| --- | --- | --- |
| 1–4 | Bìa, mục lục, mục lục 1.1 | Không có nội dung thi |
| 5–8 | KHDL là gì, bài toán chứng khoán, 3 trụ cột | [01 · mục 1](01%20Chu%20tr%C3%ACnh%20khoa%20h%E1%BB%8Dc%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 9–10 | Chu trình 7 bước | [01 · mục 2](01%20Chu%20tr%C3%ACnh%20khoa%20h%E1%BB%8Dc%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 11–18 | Ví dụ siêu thị ABC | [01 · Siêu thị ABC](01%20Chu%20tr%C3%ACnh%20khoa%20h%E1%BB%8Dc%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 19–23 | Đặc thù KHDL trong KT&KD | [01 · mục 3](01%20Chu%20tr%C3%ACnh%20khoa%20h%E1%BB%8Dc%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 24–25 | 3 lĩnh vực chuyên sâu | [01 · mục 4](01%20Chu%20tr%C3%ACnh%20khoa%20h%E1%BB%8Dc%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 26 | Dữ liệu là gì | [06 · mục 1](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md) |
| 27–28 | Phân loại theo cấu trúc (tr. 28 lặp) | [06 · mục 2](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md) |
| 29 | Định dạng tệp | [06 · mục 3](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md) |
| 30 | Nguồn dữ liệu | [06 · mục 4](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md) |
| 31 | Ngôn ngữ | [06 · mục 5](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md) |
| 32 | 4 vị trí công việc | [06 · mục 6](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md) |
| 33 | Mục lục học phần | Không có nội dung thi |
| 34–37 | Giới thiệu kỹ thuật dữ liệu, 70–80% | [02 · mục 1](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 38 | Bảng 5 bước | [02 · mục 2](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 39–41 | Nguồn sinh dữ liệu | [02 · Bước 1](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 42–44 | Lưu trữ | [02 · Bước 2](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 45–49 | Thu nạp, batch/stream, push/pull, ETL/ELT | [02 · Bước 3](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 50–53 | Biến đổi, feature engineering | [02 · Bước 4](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 54–57 | Phục vụ dữ liệu (tr. 55 lặp) | [02 · Bước 5](02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 58 | Mục lục học phần | Không có nội dung thi |
| 59–60 | Vì sao cần phân tích dữ liệu | [07 · mục 1](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 61 | Phân tích dữ liệu và KHDL | [07 · mục 2](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 62–64 | Quy trình 4 bước, khi nào dùng | [07 · mục 3](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 65–69 | Bước 1 xác định dữ liệu | [07 · mục 4](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 70–75 | Bước 2 khai phá, biến đổi, kiểm định, công bố, công cụ | [07 · mục 5](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 76–80 | 4 cấp độ phân tích | [07 · mục 6](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 81–85 | Truyền đạt, storytelling, Gapminder, Covid | [07 · mục 7](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 86–87 | Mục lục học phần, mục lục 1.4 | Không có nội dung thi (tr. 87 chỉ liệt kê đề mục) |
| 88 | Học máy là gì | [03 · mục 1](03%20Nh%C3%A3n%20v%C3%A0%20lo%E1%BA%A1i%20b%C3%A0i%20to%C3%A1n.md) |
| 89 | 3 loại học máy | [03 · mục 2](03%20Nh%C3%A3n%20v%C3%A0%20lo%E1%BA%A1i%20b%C3%A0i%20to%C3%A1n.md) |
| 90–98 | Ca quảng cáo | [Bốn ca · 1](B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture.md) |
| 99–107 | Ca Iris, KNN | [Bốn ca · 2](B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture.md) |
| 108–115 | Ca giá nhà, RF, MAE/MSE/R² | [Bốn ca · 3](B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture.md) |
| 116–123 | Ca ngân hàng, logistic | [Bốn ca · 4](B%E1%BB%91n%20ca%20h%E1%BB%8Dc%20m%C3%A1y%20trong%20lecture.md) |
| 124–125 | Mục lục học phần | Không có nội dung thi |
| 126 | Tóm tắt bài giảng |  |
| 127 | Trang cuối trống | Không có nội dung thi |

## Tóm tắt bài giảng

Nguồn tr. 126.

> **abstract** Tóm tắt
> - KHDL là lĩnh vực **liên ngành**, áp dụng phương pháp khoa học để **trích xuất tri thức từ dữ liệu**.
> - Quy trình: xác định vấn đề → thu thập → xử lý → phân tích → truyền đạt kết quả.
> - 3 lĩnh vực chuyên sâu: **Kỹ thuật dữ liệu** (thiết kế, xây, quản lý hạ tầng: thu thập, lưu trữ, xử lý hiệu quả), **Phân tích dữ liệu** (khám phá, trực quan, diễn giải để rút thông tin giá trị), **Học máy** (thuật toán cho máy học từ dữ liệu và dự đoán).
> - Nhà khoa học dữ liệu cần nắm vững **cả ba** lĩnh vực.

## Luyện theo họ bài

| Họ | Note lý thuyết cần đọc trước |
| --- | --- |
| F101 Lĩnh vực và vai trò | 01 mục 1, 4; 06 mục 6 |
| F102 Thứ tự quy trình | 01 mục 2; 02 mục 2; 07 mục 3 |
| F103 Cấp độ phân tích | 07 mục 6 |
| F104 Nguồn và thu nạp | 06 mục 2–4; 02 Bước 1, 3 |
| F105 Chất lượng dữ liệu | 02 mục 3; 07 mục 5 |
| F106 Nhãn và loại bài toán | 03; Bốn ca |
| F107 Đặt mục tiêu | 01 mục 3 |

Xem thêm các cụm bài của chương 1.

## Phân tích chuyên sâu

Một cửa hàng thấy khách rời tăng sau đổi phí. Tách bốn câu hỏi: đã xảy ra gì, vì sao, ai có nguy cơ rời và nên can thiệp ra sao.

> **check** Lập luận và ca biên
> Tỷ lệ rời tăng là mô tả. Kiểm tra theo nhóm và thời điểm là chẩn đoán. Dự đoán từng khách cần nhãn lịch sử. Chọn can thiệp cần xét chi phí, khả năng tác động và cách kiểm tra hiệu quả. Quan sát trước/sau riêng lẻ có thể lẫn với mùa vụ.
