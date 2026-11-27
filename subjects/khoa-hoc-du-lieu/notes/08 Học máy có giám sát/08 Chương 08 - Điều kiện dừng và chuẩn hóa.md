# Điều kiện dừng và chuẩn hóa dữ liệu

> **abstract** Tóm tắt
> - **Linear/Logistic** (mô hình lặp): dừng khi hết `max_iter` hoặc khi hàm mất mát cải thiện **rất nhỏ**.
> - **Cây quyết định**: dừng khi nút **thuần**, đạt **`max_depth`**, hoặc nút quá ít mẫu (**`min_samples_split`**).
> - **KNN**: học lười, **không có** quá trình huấn luyện thật → **không có điều kiện dừng**.
> - **Cần chuẩn hóa**: KNN (khoảng cách), Linear/Logistic (hạ gradient). **Không cần**: cây, rừng.

## 1. Khi nào thuật toán dừng học

Nguồn: tr. 95

"Học" không kéo dài mãi. Mỗi họ mô hình có điều kiện dừng riêng:

[![C8 08 Chương 08 - Điều kiện dừng và chuẩn h – bảng 1](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2008%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2008%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Mô hình | Khi nào dừng | Tham số liên quan |
> | --- | --- | --- |
> | Linear / Logistic Regression (mô hình **lặp**) | Sau số vòng lặp định sẵn, **hoặc** khi mức cải thiện (thay đổi hàm mất mát) giữa các vòng **rất nhỏ, không đáng kể** | `max_iter` (và dung sai `tol` – Mở rộng) |
> | Decision Tree | Một nút **không thể chia nhỏ hơn**, khi: (1) mọi điểm trong nút **cùng một lớp** (nút thuần); (2) đạt **độ sâu tối đa**; (3) số mẫu trong nút **quá nhỏ** để chia tiếp | *`max_depth`*, `min_samples_split` |
> | KNN | **Không có** điều kiện dừng: là "mô hình học lười", chỉ **lưu trữ toàn bộ dữ liệu** | (*`n_neighbors`* chỉ dùng lúc dự đoán) |

[![Chọn chuẩn hóa và điều kiện dừng](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/Ch%E1%BB%8Dn%20chu%E1%BA%A9n%20h%C3%B3a%20v%C3%A0%20%C4%91i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng.excalidraw.svg)](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/Ch%E1%BB%8Dn%20chu%E1%BA%A9n%20h%C3%B3a%20v%C3%A0%20%C4%91i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng.excalidraw.md)

> **warning** Dễ nhầm
> - *`n_estimators`* của rừng là **số cây**, không phải điều kiện dừng của mỗi cây. Mỗi cây trong rừng vẫn dừng theo *`max_depth`*, `min_samples_split`…
> - Ví dụ slide dùng *`max_depth=1`* → cây chỉ một lần chia (gốc + 2 lá).
> - `min_samples_split` là số mẫu tối thiểu **để được chia** một nút (mặc định 2), khác `min_samples_leaf` (số mẫu tối thiểu ở mỗi lá — Mở rộng).

> **question** Tự kiểm tra: một nút cây có 5 mẫu đều "Đạt", `max_depth` chưa đạt. Cây có chia tiếp không? KNN "dừng huấn luyện" khi nào?
> Không chia vì nút đã thuần. KNN không huấn luyện nên không có điểm dừng; **`fit`** chỉ lưu dữ liệu.

## 2. Khi nào cần chuẩn hóa dữ liệu

Nguồn: tr. 96, tr. 97

**Chuẩn hóa dữ liệu (Data Scaling)**: đưa các cột đặc trưng về **cùng một thang đo**. Đây là bước **cực kỳ quan trọng**.

**Tại sao?** Hai đặc trưng: kinh nghiệm (1–10 năm) và lương tháng trước (15.000.000–50.000.000). Với KNN, chênh lệch tuyệt đối của lương **lấn át** kinh nghiệm → khoảng cách gần như chỉ dựa vào lương, bỏ qua kinh nghiệm.

> **example** Theo dấu: chuẩn hóa đổi hàng xóm gần nhất
> Train: A = (1 năm, 15 triệu), B = (2 năm, 16 triệu), C = (9 năm, 15,5 triệu). Query Q = (8 năm, 15,9 triệu).
>
> | Điểm | Khoảng cách số gốc | Khoảng cách sau **`StandardScaler`** |
> | --- | ---: | ---: |
> | A | 900.000 | 2.95 |
> | B | **100.000** ← gần nhất | 1.70 |
> | C | 400.000 | **1.02** ← gần nhất |
>
> Số gốc: chênh 6 năm của B gần như không đáng kể so với chênh 100.000 đồng → chọn B. Sau chuẩn hóa: C (cùng 8–9 năm, lương gần) mới thật sự giống Q.
>
> ```python
> import numpy as np
> from sklearn.preprocessing import StandardScaler
> Xs = np.array([[1, 15_000_000], [2, 16_000_000], [9, 15_500_000]]); q = np.array(8, 15_900_000)
> print(np.sqrt(((Xs - q)**2).sum(1)).round(1))          # [900000. 100000. 400000.]
> sc = StandardScaler().fit(Xs)
> print(np.sqrt(((sc.transform(Xs) - sc.transform(q))**2).sum(1)).round(2))  # [2.95 1.7  1.02]
> ```

[![C8 08 Chương 08 - Điều kiện dừng và chuẩn h – bảng 2](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2008%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.svg)](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C8%2008%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%20%E2%80%93%20b%E1%BA%A3ng%202.excalidraw.md)

> **note** Bảng dạng chữ
> | | Mô hình | Lý do |
> | --- | --- | --- |
> | **Cần** chuẩn hóa | **KNN** (dựa trên khoảng cách) | Đặc trưng thang lớn chi phối khoảng cách |
> | **Cần** chuẩn hóa | **Linear Regression, Logistic Regression** (tối ưu bằng **hạ gradient – Gradient Descent**) | Nhạy với thang đo khi tối ưu |
> | **Không cần** | **Decision Tree, Random Forest** (dựa trên quy tắc) | Xét **từng đặc trưng độc lập** tại mỗi lần chia; ngưỡng chỉ phụ thuộc thứ tự giá trị |

> **info** Mở rộng
> - **`LinearRegression`** của sklearn giải bình phương tối thiểu trực tiếp (OLS), nên dự đoán không đổi khi scale; nhưng hệ số đổi theo thang đo. Slide xếp nó vào nhóm "cần" vì khi tối ưu bằng gradient descent thì thang đo ảnh hưởng.
> - Scaler cũng phải **`fit`** trên **train** rồi **`transform`** test (tránh rò rỉ) — xem [chia train/test](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md).

> **tip** Mẹo thi
> Câu hỏi "mô hình nào **không** cần chuẩn hóa?" → **cây và rừng**. "Vì sao KNN cần?" → vì dùng **khoảng cách**.

> **question** Tự kiểm tra: đổi đơn vị một đặc trưng từ mét sang centimet. Dự đoán của cây quyết định có đổi không? Của KNN?
> Cây: không (ngưỡng nhân 100, thứ tự giữ nguyên). KNN: có thể đổi vì khoảng cách theo chiều đó tăng 100 lần.

## 3. Tóm tắt bài giảng và tài liệu tham khảo

Nguồn: tr. 108, tr. 109

Bài giảng 8 đã giới thiệu:
- Học máy là gì và các loại hình chính → [01 Chương 08 - Train test và rò rỉ](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md).
- Các mô hình phổ biến, quy trình làm việc, quá khớp/dưới khớp.
- Cách mô hình hoạt động bên trong và đánh giá qua **ví dụ tính tay** → [03 Chương 08 - Hồi quy và KNN](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md), [04 Chương 08 - Logistic cây và rừng](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md).
- Triển khai nhanh, có cấu trúc bằng **Scikit-learn** → [06 Chương 08 - Công thức và cú pháp](06%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md).
- Tầm quan trọng của **chọn đúng chỉ số đánh giá** và **chuẩn hóa dữ liệu** → [05 Chương 08 - Ma trận nhầm lẫn và chỉ số](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md), mục 2 ở trên.

Tài liệu tham khảo: scikit-learn Getting Started (https://scikit-learn.org/stable/getting_started.html) và sách "Khoa học dữ liệu với Python", chương 12 Supervised (https://nct-neu.github.io/Sach_Khoa_hoc_du_lieu_python/chapters/chapter12-Supervised.html).

**Áp dụng ở:** F805 KNN, F807 Cây quyết định, F802 Rò rỉ dữ liệu. Luyện thêm: [Thực hành thêm - Tính điểm chia cây và đọc rừng](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20T%C3%ADnh%20%C4%91i%E1%BB%83m%20chia%20c%C3%A2y%20v%C3%A0%20%C4%91%E1%BB%8Dc%20r%E1%BB%ABng.md).
