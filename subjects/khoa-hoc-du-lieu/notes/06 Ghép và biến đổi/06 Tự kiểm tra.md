# Tự kiểm tra · Chương 6

Đóng slide, viết đáp án và lý do trước khi mở từng thẻ. Ghi lại câu sai hoặc trả lời do đoán để kiểm tra sau 1, 3 và 7 ngày.

> **question** Bắt đầu. Bảng index [10, 20] có hai hàng. loc[10] và iloc[0] có trỏ cùng hàng?
> Có. loc tìm nhãn 10, iloc lấy hàng ở vị trí 0. Số nhãn và vị trí có ý nghĩa riêng.

> **question** 1. Hai dòng trái và ba dòng phải cùng một khóa cho bao nhiêu cặp?
> Sáu cặp. *`left`* chỉ bổ sung dòng trái không khớp, nếu có.

> **question** 2. `concat(axis=1)` với index trái [0,1] và phải [1,2] cho index nào?
> Mặc định outer, hợp nhãn là [0,1,2] và các vị trí không khớp bị thiếu.

> **question** 3. Tình huống nào `pivot` ném lỗi nhưng `pivot_table` có thể chạy?
> Khi có nhiều dòng cho cùng cặp nhãn hàng–cột và đã xác định phép tổng hợp.

> **question** 4. Đổi thứ tự hai cấp MultiIndex khác sắp xếp thế nào?
> **`swaplevel`** đổi vị trí cấp trong tuple nhãn. **`sort_index`** sắp xếp các hàng hoặc cột theo nhãn.

> **question** 5. Trái có A=8 và B thiếu. Phải có A=9, B=2, C=3. combine_first cho gì?
> A=8, B=2, C=3. Hai Series căn theo nhãn. Bên trái được ưu tiên nếu có giá trị.

> **question** 6. Bảng rộng có ba cửa hàng và hai cột quý. melt giữ mã cửa hàng, trải cả hai quý. Bảng dài có mấy hàng?
> Sáu, mỗi hàng là một cặp cửa hàng–quý. Một ô quý thiếu vẫn tạo một hàng có giá trị thiếu.

> **question** 7. Đơn có nhiều hàng một mã khách. Bảng khách phải có một dòng mỗi mã. Dùng validate nào khi merge?
> *`validate="many_to_one"`* nếu đơn là bảng trái. Đổi thành `one_to_many` nếu khách ở bên trái.

> **question** 8. `stock_prices` có index (Ma CP, Ngay). Vì sao `stock_prices.loc['2025-08-14']` lỗi và sửa thế nào?
> *`loc`* với nhãn đơn chỉ khớp cấp ngoài (Ma CP). Dùng **`xs('2025-08-14', level='Ngay')`** hoặc `swaplevel(0, 1).loc['2025-08-14']`. Xem [01 MultiIndex](01%20MultiIndex.md).

> **question** 9. purchases có Alice ×2, Bob ×1, Charlie ×2; favorites có Alice ×2, Bob ×1, Charlie ×1. Inner merge theo customer có mấy hàng?
> 2·2 + 1·1 + 2·1 = 7. Xem Đếm hàng khi merge nhiều–nhiều.excalidraw.

> **question** 10. `pd.concat([sales_hanoi, sales_saigon, sales_danang])` (mỗi bảng 2 dòng, index 0, 1) có index gì? Muốn 0..5 thì sao?
> `0, 1, 0, 1, 0, 1`. Thêm *`ignore_index=True`*.

> **question** 11. `df.melt(id_vars='id')` với df có cột id, math, english (3 dòng). Tên hai cột mới và số dòng?
> `variable`, `value`; 6 dòng.

> **question** 12. `df.stack()` mặc định đưa cấp nào xuống hàng? Cấp mới nằm ở đâu trong index hàng?
> Cấp cột trong cùng (*`level=-1`*), thành cấp trong cùng của index hàng.

> **question** 13. `gdp_backup.combine_first(gdp_main)` cho năm 2018 giá trị nào (main 2450, backup 2445)?
> 2445 — bên gọi (backup) được ưu tiên vì nó không thiếu.

Sau lượt đầu, thay dữ kiện trong một câu và giải lại từ đầu. Ôn quy tắc trong [05 Công thức và cú pháp](05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md) và Thẻ nhớ chương 6.

Mục lục chương 6
