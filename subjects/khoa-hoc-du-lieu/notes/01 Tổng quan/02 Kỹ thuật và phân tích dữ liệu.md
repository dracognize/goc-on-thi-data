# Kỹ thuật và phân tích dữ liệu

> **abstract** Tóm tắt
> - **Kỹ thuật dữ liệu (Data Engineering)** chuẩn bị và bảo đảm dữ liệu **sẵn sàng, sạch, đúng định dạng** cho phân tích. Chiếm **70–80%** thời gian dự án KHDL.
> - Quy trình 5 bước: **Nguồn sinh (Source Systems) → Lưu trữ (Storage) → Thu nạp (Ingestion) → Biến đổi (Transformation) → Phục vụ (Serving)**.
> - Thu nạp: **batch / streaming** (theo cách xử lý), **push / pull** (theo cơ chế truyền), **ETL / ELT** (thứ tự biến đổi và nạp).
> - Lưu trữ: SQL, NoSQL, Data Warehouse, Data Mart, Data Lake.
> - Phục vụ: Business Analytics, Operational Analytics, ML Serving, **Reverse ETL**.
> - Phần phân tích dữ liệu chi tiết ở [07 Quy trình phân tích dữ liệu](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md).

## Theo một hóa đơn qua hệ thống



> **note** Bảng dạng chữ
> | Khâu | Ví dụ một hóa đơn 001 |
> | --- | --- |
> | Nguồn | Máy bán hàng ghi mã 001 và số tiền 80.000 đồng |
> | Lưu trữ | Kho dữ liệu giữ bảng hóa đơn của mọi cửa hàng |
> | Thu nạp | Cuối buổi sao chép cả tệp (batch) hoặc gửi từng hóa đơn khi phát sinh (streaming) |
> | Biến đổi | Đổi "80,000" dạng chuỗi thành số; đổi ngày sang kiểu datetime |
> | Phục vụ | Dashboard tổng doanh thu theo cửa hàng |

**Schema** là mô tả hình dạng cột và quy tắc dữ liệu. **Khóa** nhận diện bản ghi, ví dụ mã hóa đơn.

## 1. Giới thiệu kỹ thuật dữ liệu

Nguồn tr. 34–tr. 37.

- Kỹ thuật dữ liệu là lĩnh vực **riêng biệt nhưng gắn chặt** với KHDL. KHDL "phân tích và dự đoán từ dữ liệu"; kỹ thuật dữ liệu **chuẩn bị** để dữ liệu sẵn sàng, sạch, đúng định dạng.
- **70–80% thời gian** dự án KHDL dành cho chuẩn bị, xử lý dữ liệu.
- Vai trò **cầu nối** giữa dữ liệu thô và dữ liệu có giá trị: đầu vào cho phân tích và học máy phải **chính xác, đầy đủ, luôn sẵn sàng**.
- Là quá trình biến dữ liệu thô từ nhiều nguồn thành thông tin dùng được, gồm 5 bước như **dây chuyền** trong nhà máy dữ liệu.

## 2. Năm bước của quy trình kỹ thuật dữ liệu

Nguồn tr. 38.



> **note** Bảng dạng chữ
> | Giai đoạn | Tên tiếng Anh | Mô tả |
> | --- | --- | --- |
> | 1. Xác định nguồn sinh dữ liệu | Source Systems | Hệ thống gốc tạo dữ liệu: phần mềm nghiệp vụ, cảm biến, giao dịch thương mại |
> | 2. Tổ chức lưu trữ | Storage | Lưu có tổ chức: cơ sở dữ liệu, kho dữ liệu, hồ dữ liệu |
> | 3. Thu nạp | Data Ingestion | Trích xuất từ nguồn, chuyển vào lưu trữ trung tâm; batch hoặc streaming |
> | 4. Biến đổi | Data Transformation | Xử lý, làm sạch, chuẩn hóa để sẵn sàng phân tích |
> | 5. Phục vụ | Data Serving | Cung cấp dữ liệu đã xử lý cho người dùng cuối, ứng dụng, học máy |



> **warning** Dễ nhầm thứ tự
> Theo slide, **Lưu trữ (bước 2) đứng trước Thu nạp (bước 3)**: phải thiết kế nơi chứa trước rồi mới đổ dữ liệu vào. Nhiều phương án nhiễu đảo thành "Nguồn → Thu nạp → Lưu trữ".

### Bước 1 – Nguồn sinh dữ liệu (Source Systems)

Nguồn tr. 39–tr. 41.

Hệ thống nguồn là **điểm khởi đầu**, nơi dữ liệu thô sinh ra từ hoạt động thực tế. Nó cấp "nguyên liệu đầu vào" và **ảnh hưởng trực tiếp đến chất lượng, độ phức tạp, độ tin cậy** của cả pipeline.



> **note** Bảng dạng chữ
> | Nguồn trong KT&KD | Mô tả |
> | --- | --- |
> | CSDL giao dịch | Giao dịch ngân hàng, đơn hàng TMĐT, thanh toán điện tử |
> | Hệ thống CRM | Hành vi khách: lịch sử mua, tương tác, điểm khách hàng thân thiết |
> | API dữ liệu vĩ mô | IMF, World Bank, Tổng cục Thống kê: GDP, CPI, thất nghiệp |
> | File nội bộ (Excel, CSV) | Báo cáo thủ công, file tổng hợp từ các phòng ban |
> | Website/App | Lượt xem, tìm kiếm, click, feedback |

**Sáu đặc tính cần phân tích ở nguồn** (tr. 41):



> **note** Bảng dạng chữ
> | Đặc tính | Câu hỏi | Ví dụ |
> | --- | --- | --- |
> | Cách sinh dữ liệu | Theo sự kiện, theo lịch, theo lô? | Giao dịch → Event; báo cáo tài chính → Monthly batch |
> | Tần suất cập nhật | Real-time, ngày, tuần? | Click website → real-time |
> | Tính ổn định cấu trúc | Schema có đổi? Đọc tự động được? | Excel thêm cột mỗi tháng |
> | Khả năng truy cập | Qua SQL, API, tải file? | Dữ liệu vĩ mô GSO → file Excel |
> | Định dạng | Cấu trúc, bán, phi cấu trúc? | CRM → bảng; JSON API → bán cấu trúc; khảo sát PDF → phi cấu trúc |
> | Chất lượng | Đầy đủ? Đúng? Kịp thời? | Thiếu số điện thoại, sai mã tỉnh |

### Bước 2 – Tổ chức lưu trữ (Storage)

Nguồn tr. 42–tr. 44.

Giai đoạn **trung tâm**: dữ liệu được bảo toàn, tổ chức, chuẩn bị. Vai trò: lưu từ nhiều nguồn; giúp tìm kiếm, truy vấn hiệu quả; là **"kho nguyên liệu sạch"** cho phân tích, AI, học máy.



> **note** Bảng dạng chữ
> | Hình thức | Mô tả | Ví dụ |
> | --- | --- | --- |
> | CSDL quan hệ (SQL) | Có cấu trúc, hàng – cột | Bán hàng, kế toán (MySQL, PostgreSQL, Oracle) |
> | CSDL phi quan hệ (NoSQL) | Bán/phi cấu trúc, linh hoạt | Ứng dụng di động, mạng xã hội (MongoDB, Redis) |
> | **Data Warehouse** | Tổng hợp, **chuẩn hóa** từ nhiều nguồn để phân tích | Phân tích kinh doanh (BigQuery, Snowflake) |
> | **Data Mart** | Kho chuyên biệt **theo phòng ban**, tối ưu truy vấn | Marketing, tài chính (Power BI, Tableau) |
> | **Data Lake** | Lưu **dữ liệu thô, mọi định dạng** (văn bản, video, ảnh) | Dữ liệu lớn, AI (Amazon S3, Azure DL) |

**Năm yếu tố khi thiết kế lưu trữ** (tr. 44):
- **Tần suất truy cập**: dùng thường xuyên → *dữ liệu nóng*; lưu lâu dài → *dữ liệu nguội*.
- **Khả năng mở rộng**: dữ liệu tăng theo doanh nghiệp → hệ thống tự mở rộng.
- **Bảo mật và pháp lý**: dữ liệu tài chính, khách hàng tuân thủ luật (GDPR), phân quyền, mã hóa.
- **Cấu trúc dữ liệu**: dạng bảng → SQL; linh hoạt (JSON) → NoSQL, Data Lake.
- **Khả năng tích hợp**: kết nối dễ với Power BI, Python, mô hình AI, công cụ báo cáo.

> **warning** Dễ nhầm
> **Warehouse** chứa dữ liệu **đã chuẩn hóa** cho toàn doanh nghiệp. **Mart** là một **phần nhỏ theo phòng ban**. **Lake** chứa **thô, mọi định dạng**. Ảnh và video → Lake, không phải Warehouse.

> **question** Tự kiểm tra: Phòng marketing muốn kho riêng, truy vấn nhanh cho báo cáo của mình. Chọn gì?
> Data Mart.

### Bước 3 – Thu nạp (Data Ingestion)

Nguồn tr. 45–tr. 49.

Chuyển dữ liệu từ **nguồn sang lưu trữ**. Là **cửa ngõ đầu tiên**; thu nạp lỗi → mọi phân tích sau mất giá trị. Cần: **đúng lúc, đúng định dạng, không trùng lặp, dễ kiểm soát & tái sử dụng**.



> **note** Bảng dạng chữ
> | Thách thức | Ví dụ |
> | --- | --- |
> | Nguồn không ổn định | Website TMĐT đổi API → ngừng thu thập |
> | Thiếu chuẩn hóa định dạng | 3 chi nhánh → 3 kiểu định dạng ngày |
> | Trùng lặp hoặc thiếu sót | Đơn hàng bị đẩy lên hệ thống 2 lần |

Ba cách phân loại cần tách bạch:

| Trục phân loại | Lựa chọn | Mô tả | Ví dụ |
| --- | --- | --- | --- |
| Phương thức xử lý (tr. 47) | **Batch** | Theo lô, định kỳ (giờ, ngày, tuần); báo cáo định kỳ, khối lượng lớn, không cần thời gian thực | Lấy báo cáo đơn hàng mỗi tối |
| | **Streaming** | Liên tục, thời gian thực, từng dòng | Phát hiện gian lận giao dịch ngân hàng |
| Cơ chế truyền (tr. 48) | **Push** | **Nguồn** chủ động đẩy đi | CRM tự đẩy thông tin khách mới |
| | **Pull** | **Đích** chủ động lấy theo lịch | ETL chạy mỗi 24h lấy dữ liệu API Tổng cục Thống kê |
| Thứ tự (tr. 49) | **ETL** | Extract → **Transform → Load**: biến đổi trước khi lưu; kiểm soát chặt chất lượng; Data Warehouse truyền thống | Chuẩn kiểu ngày rồi mới nạp kho |
| | **ELT** | Extract → **Load → Transform**: lưu trước rồi biến đổi; hệ lớn (Data Lake, Cloud DW), linh hoạt phân tích sau | Đổ log thô vào lake rồi tổng hợp bằng truy vấn |



> **tip** Mẹo thi
> - Hỏi **"ai chủ động?"** → push/pull. Hỏi **"bao lâu một lần?"** → batch/streaming. Hỏi **"biến đổi trước hay sau khi nạp?"** → ETL/ELT.
> - Một hệ thống có thể vừa **pull** vừa **batch** (ETL lấy mỗi 24h).

> **question** Tự kiểm tra: Ngân hàng nạp mọi log giao dịch thô vào Data Lake trên cloud, khi cần mới làm sạch. Mô hình gì?
> ELT.

### Bước 4 – Biến đổi (Data Transformation)

Nguồn tr. 50–tr. 53.

Chuyển dữ liệu thô thành dữ liệu sẵn sàng: đầy đủ, sạch, có cấu trúc rõ, đúng mục đích.



> **note** Bảng dạng chữ
> | Mục tiêu | Cụ thể |
> | --- | --- |
> | Làm sạch | Loại lỗi, giá trị trống, sai định dạng (số âm cho tuổi) |
> | Chuẩn hóa | Đồng bộ đơn vị (VND, USD), định dạng ngày (dd/mm/yyyy) |
> | Chuyển kiểu dữ liệu | "ngày đặt hàng" chuỗi → datetime |
> | Tạo đặc trưng (Feature Engineering) | "Tuổi" từ ngày sinh |



> **note** Bảng dạng chữ
> | Thao tác phổ biến | Ví dụ |
> | --- | --- |
> | Chuyển kiểu | "2023-08-01" → ngày; "100,000" → số nguyên |
> | Xử lý thiếu/ngoại lệ | Bỏ dòng thiếu, thay bằng trung bình/median |
> | Gộp nhóm và tính toán | Doanh thu tháng = SUM(doanh thu từng đơn) |
> | Pivot / Unpivot | Chuyển chiều ngang ↔ chiều dọc |
> | Chuẩn hóa định dạng | Mọi tiền tệ về VND hoặc USD |

**Theo cách xử lý** (tr. 52): **Batch transformation** (theo lô, chu kỳ: báo cáo tài chính, doanh thu cuối ngày) và **Streaming transformation** (thời gian thực: phát hiện gian lận, dashboard trực tiếp).

**Feature Engineering** (tr. 53) là **bước sáng tạo**: tạo biến đầu vào chất lượng cao cho học máy, kết hợp **hiểu biết nghiệp vụ + kỹ thuật**. Ví dụ: ngày sinh → tuổi; số lần mua → trung bình đơn hàng; lịch sử truy cập → thời gian truy cập cao nhất.

> **example** Code: biến đổi bảng đơn hàng (đã chạy kiểm chứng)
> ```python
> import pandas as pd
> df = pd.DataFrame({
>     "ma_don": ["D1", "D2", "D2", "D3", "D4"],
>     "ngay":   ["2023-08-01", "2023-08-01", "2023-08-01", "2023-08-02", None],
>     "tien":   ["100,000", "250,000", "250,000", "80,000", "50,000"],
> })
> print("Trùng mã đơn:", df["ma_don"].duplicated().sum())
> print("Thiếu ngày:", df["ngay"].isna().sum())
> df = df.drop_duplicates()                                  # bỏ đơn đẩy 2 lần
> df["ngay"] = pd.to_datetime(df["ngay"])                    # chuỗi → ngày
> df["tien"] = df["tien"].str.replace(",", "").astype(int)   # "100,000" → 100000
> print(df.dtypes.to_dict())
> print(df.groupby("ngay")["tien"].sum())                    # gộp nhóm
> ```
> Kết quả:
> ```text
> Trùng mã đơn: 1
> Thiếu ngày: 1
> {'ma_don': dtype('O'), 'ngay': dtype('<M8[ns]'), 'tien': dtype('int64')}
> ngay
> 2023-08-01    350000
> 2023-08-02     80000
> Name: tien, dtype: int64
> ```
> Đơn D4 thiếu ngày nên **`groupby`** bỏ qua nó. Đó là lý do phải xử lý thiếu **trước** khi tổng hợp.

### Bước 5 – Phục vụ dữ liệu (Data Serving)

Nguồn tr. 54–tr. 57 (tr. 55 lặp tr. 54).

Bước cuối: dữ liệu đã xử lý đến **đúng người, đúng lúc**, sẵn sàng cho hành động, phân tích, dự đoán, quyết định.



> **note** Bảng dạng chữ
> | Mục tiêu | Cụ thể |
> | --- | --- |
> | Hỗ trợ phân tích & báo cáo | Nhà quản trị theo dõi hiệu suất, chiến lược |
> | Cung cấp dữ liệu cho mô hình học máy | Đầu vào cho dự đoán, phân loại, cá nhân hóa |
> | **Đồng bộ ngược (Reverse ETL)** | Đưa dữ liệu phân tích **trở lại hệ thống vận hành** như CRM, marketing |



> **note** Bảng dạng chữ
> | Hình thức | Ví dụ | Đặc điểm |
> | --- | --- | --- |
> | Business Analytics | Dashboard doanh thu tháng, báo cáo KPI | Tổng hợp, lịch sử, quyết định **chiến lược** |
> | Operational Analytics | Cảnh báo tồn kho thấp, theo dõi gian lận | **Gần thời gian thực**, phục vụ vận hành |
> | Machine Learning Serving | Gợi ý sản phẩm, phát hiện rủi ro tín dụng | Dữ liệu vào + dự đoán → ứng dụng **tức thì** |
> | Reverse ETL | Phân khúc khách từ BI về CRM để chăm sóc | Đồng bộ ngược kho → hệ tác nghiệp |

**Nguyên tắc thiết kế**: (1) đúng người – đúng thời điểm – đúng mục tiêu (ai cần, cần gì, lúc nào, để làm gì); (2) phối hợp đa bộ phận (kỹ sư dữ liệu + nhà phân tích + nghiệp vụ + ML engineer); (3) hiệu suất – bảo mật – mở rộng (truy cập nhanh, độ trễ thấp, phân quyền). Đây là nơi **dữ liệu chuyển hóa thành giá trị thực tế**.

> **warning** Dễ nhầm
> Reverse ETL **không** phải "ETL làm ngược thứ tự" (đó là ELT). Reverse ETL là **đưa dữ liệu từ kho về lại hệ thống tác nghiệp** (CRM).

> **question** Tự kiểm tra: Cảnh báo tồn kho thấp gần thời gian thực thuộc hình thức phục vụ nào?
> Operational Analytics.

## 3. Chất lượng dữ liệu

Nguồn tr. 41 (đầy đủ, đúng, kịp thời) và tr. 73 (5 tiêu chí kiểm định). Chiều "hợp lệ" là **Mở rộng**.



> **note** Bảng dạng chữ
> | Tiêu chí | Ý nghĩa | Ví dụ lỗi |
> | --- | --- | --- |
> | Đầy đủ (completeness) | Không bị thiếu | Thiếu tổng tiền |
> | Chính xác (accuracy) | Đúng logic, không sai lệch | 80.000 nhập thành 800.000; tuổi 200 |
> | Nhất quán (consistency) | Định dạng, logic đồng nhất giữa nguồn | Hai nguồn hai kiểu ngày |
> | Duy nhất (uniqueness) | Không trùng không cần thiết | Một hóa đơn nhập hai lần |
> | Kịp thời (timeliness) | Cập nhật mới, đúng thời gian | Báo cáo thiếu giao dịch chiều nay |

> **info** Mở rộng
> Nhiều tài liệu thêm chiều **hợp lệ (validity)**: giá trị nằm trong miền cho phép, ví dụ mã cửa hàng ngoài danh mục.

## 4. Bốn cấp độ phân tích (tóm tắt)

Chi tiết ở [07 · Bốn cấp độ](07%20Quy%20tr%C3%ACnh%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md). Nguồn tr. 76.



> **note** Bảng dạng chữ
> | Cấp độ | Câu hỏi |
> | --- | --- |
> | Mô tả (Descriptive) | Điều gì đã xảy ra? |
> | Chẩn đoán (Diagnostic) | Tại sao xảy ra? |
> | Dự báo (Predictive) | Điều gì có thể xảy ra? |
> | Định hướng hành động (Prescriptive) | Chúng ta nên làm gì? |

> **question** Tự kiểm tra tổng hợp: Nguồn bán hàng gửi mỗi sự kiện ngay khi phát sinh. Báo cáo gộp mỗi sáng. Hai khâu dùng cách nào?
> Thu nạp theo push và streaming. Báo cáo tổng hợp chạy batch. Cách truyền và lịch xử lý là hai quyết định riêng.

Áp dụng ở F104 Nguồn dữ liệu và cách thu nạp, F105 Chất lượng dữ liệu, F101 Vai trò. Cần biết trước [06 Dữ liệu và vị trí công việc](06%20D%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20v%E1%BB%8B%20tr%C3%AD%20c%C3%B4ng%20vi%E1%BB%87c.md).
