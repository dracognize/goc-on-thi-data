# Chương 5 · Làm sạch và xử lý dữ liệu

> **abstract** Chương này trả lời 5 câu hỏi
> 1. Ô nào thiếu, vì sao thiếu, xử lý thế nào? (5.1)
> 2. Hàng nào trùng, giữ bản nào? (5.2)
> 3. Đưa các cột về cùng thang đo bằng scaler nào? (5.3)
> 4. Làm sạch chuỗi và trích thông tin bằng **`.str`** và regex ra sao? (5.4)
> 5. Mã hóa biến phân loại bằng Label hay One-hot? (5.5)

Slide gốc: Lec 5, trang 1.

## Thứ tự đọc

1. [01 Thiếu và trùng](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md): 5.1 (dạng thiếu, phát hiện, *`dropna`*, **`fillna`**, chọn phương pháp) và 5.2 (**`duplicated`**, **`drop_duplicates`**).
2. [Thực hành thêm - Điền dữ liệu bằng mô hình](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md): Random Forest, KNN Imputation, **`LabelEncoder`**, **`zip`**, **`iterrows`**, **`enumerate`**.
3. [03 Chuẩn hóa dữ liệu](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md): MinMax, Standard, Robust và ví dụ outlier.
4. [04 Chuỗi và mã hóa phân loại](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md): **`.str`**, regex, **`pd.Categorical`**, Label Encoding, One-Hot Encoding.
5. [05 Công thức và cú pháp](05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md): bảng tra nhanh.
6. [06 Tự kiểm tra](06%20T%E1%BB%B1%20ki%E1%BB%83m%20tra.md) rồi Thẻ nhớ chương 5 (tag `#flashcards/chuong-5`, ôn bằng Spaced Repetition).

## Bản đồ chương



## Phủ slide

| Trang | Chủ đề | Note |
| --- | --- | --- |
| 1–3 | Bìa, mục lục bài giảng | Không có nội dung thi |
| 4–7 | 5.1.1 Các dạng thiếu, NaN/None/NaT | [01 · 5.1.1](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 8 | 5.1.2 Nguyên nhân | [01 · 5.1.2](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 9–10 | 5.1.3 Tác động, bảng `df_missing` | [01 · 5.1.3](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 11–16 | 5.1.4 **`isna`**, **`notna`**, **`sum`**, **`any`** | [01 · 5.1.4](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 17 | 5.1.5 Ba cách xử lý | [01 · 5.1.5](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 18–23 | *`dropna`* | [01 · dropna](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 24–30 | **`fillna`**: cố định, mean, median, mode, ffill, bfill | [01 · fillna](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 31–35 | Mô hình dự đoán, `df_advanced`, tỷ lệ thiếu | [Thực hành · Khi nào dùng](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) |
| 36–39 | Random Forest, cây quyết định, tham số | [Thực hành · Random Forest](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) |
| 40–51 | Demo 1 dự đoán Tuổi, **`zip`**, **`iterrows`**, **`enumerate`** | [Thực hành · Demo 1](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) |
| 52–57 | Demo 2 dự đoán Lương, feature importance | [Thực hành · Demo 2](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) |
| 58–59 | KNN Imputation, Euclidean | [Thực hành · KNN](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) |
| 60–66 | Demo 3 **`KNNImputer`** | [Thực hành · Demo 3](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) |
| 67–68 | So sánh, hướng dẫn chọn phương pháp | [01 · Chọn phương pháp](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 69 | Trang chuyển mục | Không có nội dung thi |
| 70–73 | 5.2.1 Trùng lặp: khái niệm, nguyên nhân, tác động | [01 · 5.2.1](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 74–76 | 5.2.2 **`duplicated`** | [01 · 5.2.2](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 77–79 | 5.2.3 **`drop_duplicates`** | [01 · 5.2.3](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| 80 | Trang chuyển mục | Không có nội dung thi |
| 81–84 | 5.3.1 Tổng quan biến đổi | [03 · 5.3.1](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 85–87 | 5.3.2 Min-Max | [03 · 5.3.2](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 88–92 | 5.3.3 Standard Scaler | [03 · 5.3.3](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 93–95 | 5.3.4 Robust Scaler, bảng so sánh | [03 · 5.3.4](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 96–101 | Ví dụ outlier 200 triệu, boxplot | [03 · Outlier](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| 102 | Trang chuyển mục | Không có nội dung thi |
| 103–105 | 5.4.1–5.4.2 Tầm quan trọng, vấn đề chuỗi | [04 · 5.4.2](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| 106–118 | 5.4.3 **`.str`**, đổi kiểu, ví dụ | [04 · 5.4.3](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| 119–126 | 5.4.4 Regex, điện thoại, email, URL | [04 · 5.4.4](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| 127 | Trang chuyển mục | Không có nội dung thi |
| 128–129 | 5.5.1 Nominal, Ordinal | [04 · 5.5.1](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| 130–133 | 5.5.2 Kiểu category, **`pd.Categorical`** | [04 · 5.5.2](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| 134–138 | 5.5.3 Label Encoding | [04 · 5.5.3](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| 139–145 | 5.5.4 One-Hot Encoding, đa cộng tuyến | [04 · 5.5.4](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| 146 | Trang trống cuối | Không có nội dung thi |

## Sơ đồ

| Sơ đồ | Trả lời câu hỏi |
| --- | --- |
| [02 Chương 5 - Quy trình.excalidraw](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/02%20Ch%C6%B0%C6%A1ng%205%20-%20Quy%20tr%C3%ACnh.excalidraw.md) | Quy trình làm sạch tổng thể |
| [Cây chọn cách xử lý thiếu.excalidraw](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/C%C3%A2y%20ch%E1%BB%8Dn%20c%C3%A1ch%20x%E1%BB%AD%20l%C3%BD%20thi%E1%BA%BFu.excalidraw.md) | Loại dữ liệu và tỷ lệ thiếu nào thì dùng cách nào? |
| [Theo dấu dropna trên df_missing.excalidraw](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/Theo%20d%E1%BA%A5u%20dropna%20tr%C3%AAn%20df_missing.excalidraw.md) | Năm cách gọi *`dropna`* giữ lại hàng nào? |
| [Theo dấu hàng thiếu và trùng.excalidraw](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/Theo%20d%E1%BA%A5u%20h%C3%A0ng%20thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.excalidraw.md) | **`isna`**, **`duplicated(keep='last')`** đánh dấu hàng nào? |
| [KNN điền ô thiếu của Bình.excalidraw](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/KNN%20%C4%91i%E1%BB%81n%20%C3%B4%20thi%E1%BA%BFu%20c%E1%BB%A7a%20B%C3%ACnh.excalidraw.md) | KNNImputer chọn láng giềng nào? |
| [So sánh ba scaler khi có outlier.excalidraw](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/So%20s%C3%A1nh%20ba%20scaler%20khi%20c%C3%B3%20outlier.excalidraw.md) | Outlier làm hỏng scaler nào? |
| [Label hay One-hot.excalidraw](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/Label%20hay%20One-hot.excalidraw.md) | Chọn kiểu mã hóa nào? |

[![02 Chương 5 - Quy trình](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/02%20Ch%C6%B0%C6%A1ng%205%20-%20Quy%20tr%C3%ACnh.excalidraw.svg)](../../diagrams/05%20L%C3%A0m%20s%E1%BA%A1ch/02%20Ch%C6%B0%C6%A1ng%205%20-%20Quy%20tr%C3%ACnh.excalidraw.md)

## Chuẩn đầu ra

- Phân biệt MCAR, MAR, MNAR. Phát hiện thiếu và trùng, đọc được kết quả **`isna().sum()`**, **`duplicated()`**.
- Dự đoán số hàng/cột còn lại sau *`dropna`* với *`axis`*, *`how`*, *`thresh`*, *`subset`*. Tính giá trị điền mean, median, mode, ffill, bfill.
- Giải thích các bước Demo Random Forest và KNNImputer.
- Tính tay min-max, z-score, robust. Chọn scaler khi có outlier.
- Đọc kết quả các phương thức **`.str`** và regex cơ bản.
- Chọn Label hay One-hot, đếm số cột sau **`get_dummies`** và *`drop='first'`*.

## Họ bài luyện của chương

| Họ | Học trước |
| --- | --- |
| F501 Nguyên nhân thiếu | [01 Thiếu và trùng](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| F502 Phát hiện thiếu | [01 Thiếu và trùng](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| F503 dropna | [01 Thiếu và trùng](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| F504 Điền thiếu | [01 Thiếu và trùng](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| F505 Dữ liệu trùng | [01 Thiếu và trùng](01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) |
| F506 Ngoại lai | [03 Chuẩn hóa dữ liệu](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| F507 Chuẩn hóa thang đo | [03 Chuẩn hóa dữ liệu](03%20Chu%E1%BA%A9n%20h%C3%B3a%20d%E1%BB%AF%20li%E1%BB%87u.md) |
| F508 Mã hóa phân loại | [04 Chuỗi và mã hóa phân loại](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| F509 Chuỗi và regex | [04 Chuỗi và mã hóa phân loại](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| F510 Kiểu dữ liệu cột | [04 Chuỗi và mã hóa phân loại](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| F511 Rời rạc hóa | [05 Công thức và cú pháp](05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md) |
| F512 Phân loại biến | [04 Chuỗi và mã hóa phân loại](04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) |
| F513 ML hỗ trợ làm sạch | [Thực hành thêm - Điền dữ liệu bằng mô hình](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20%C4%90i%E1%BB%81n%20d%E1%BB%AF%20li%E1%BB%87u%20b%E1%BA%B1ng%20m%C3%B4%20h%C3%ACnh.md) |

Xem thêm các họ bài của chương 5.

## Liên hệ

Cần biết trước [CSV và schema](../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/01%20CSV%20v%C3%A0%20schema.md). Áp dụng ở [ghép dữ liệu](../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/03%20Merge%20concat%20v%C3%A0%20combine_first.md) và [học máy có giám sát](../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md).

## Phân tích chuyên sâu

Với thu nhập [10, 11, 12, 100, thiếu], so sánh điền median và mean. Giải thích điều gì thay đổi nếu 100 là lỗi nhập.

> **check** Lập luận và ca biên
> Mean của các giá trị có mặt là 33,25. Median là 11,5. Xác minh 100 theo nguồn trước khi bỏ. Nếu giá trị hợp lệ, median ít nhạy với cực trị hơn. Lưu dấu thiếu khi hữu ích và học thống kê trên tập train trong bài toán dự báo.
