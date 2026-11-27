# Chẩn đoán chất lượng dữ liệu

**Quy tắc nhận diện và giải.** Xác định triệu chứng trực tiếp trước khi suy ra hậu quả, rồi ghép với tiêu chí chất lượng.

Cần biết trước [Kỹ thuật và phân tích dữ liệu](../../01%20T%E1%BB%95ng%20quan/02%20K%E1%BB%B9%20thu%E1%BA%ADt%20v%C3%A0%20ph%C3%A2n%20t%C3%ADch%20d%E1%BB%AF%20li%E1%BB%87u.md). Nguồn ScoreUp.

## 1. Cơ bản

Bảng khách hàng được gộp từ hai chi nhánh: chi nhánh Hà Nội ghi ngày theo dạng ngày/tháng/năm, chi nhánh TP.HCM ghi theo dạng tháng/ngày/năm nên nhiều ngày bị hiểu sai khi gộp. Vấn đề này chủ yếu vi phạm tiêu chí chất lượng dữ liệu nào?

- **A.** Đầy đủ
- **B.** Nhất quán
- **C.** Phù hợp
- **D.** Dễ truy cập

> **tip** Gợi ý
> Hai nơi có đang biểu diễn cùng một trường theo một quy tắc?

> **success** Đáp án và hướng giải
> **B.** Tiêu chí trực tiếp là nhất quán: hai chi nhánh dùng hai quy ước ngày. Đọc nhầm ngày là hậu quả của sự khác quy ước.

Mã câu `Q00005` · Nhóm gốc 1.

## 2. Vận dụng

Bảng khách hàng có 8% số dòng bỏ trống số điện thoại, đồng thời một số dòng ghi tuổi là 215. Hai vấn đề này lần lượt vi phạm tiêu chí chất lượng dữ liệu nào?

- **A.** Tính chính xác rồi tính đầy đủ
- **B.** Tính nhất quán rồi tính duy nhất
- **C.** Tính đầy đủ rồi tính chính xác
- **D.** Tính kịp thời rồi tính nhất quán

> **tip** Gợi ý
> Tách ô trống và ô đã có nhưng chứa giá trị vô lý.

> **success** Đáp án và hướng giải
> **C.** Thiếu số điện thoại làm giảm tính đầy đủ. Tuổi 215 là giá trị ghi sai nên vi phạm tính chính xác theo cách phân loại của câu hỏi.

Mã câu `Q00043` · Nhóm gốc 1.

## 3. Tổng hợp

Ghép đúng từng tình huống với tiêu chí chất lượng dữ liệu bị vi phạm: (1) 8% dòng thiếu giá trị thu nhập; (2) cột ngày ghi lẫn dạng dd/mm/yyyy và yyyy-mm-dd; (3) số liệu tồn kho cập nhật chậm nhiều tuần; (4) hai dòng đơn hàng giống hệt nhau.

- **A.** (1) đầy đủ, (2) chính xác, (3) kịp thời, (4) duy nhất
- **B.** (1) đầy đủ, (2) nhất quán, (3) kịp thời, (4) chính xác
- **C.** (1) chính xác, (2) nhất quán, (3) kịp thời, (4) duy nhất
- **D.** (1) đầy đủ, (2) nhất quán, (3) kịp thời, (4) duy nhất

> **tip** Gợi ý
> Ghép dấu hiệu thiếu, lệch chuẩn, trễ và trùng với bốn tiêu chí.

> **success** Đáp án và hướng giải
> **D.** Thu nhập thiếu ảnh hưởng đầy đủ. Định dạng ngày khác nhau ảnh hưởng nhất quán. Tồn kho cập nhật chậm ảnh hưởng kịp thời. Đơn lặp ảnh hưởng tính duy nhất.

Mã câu `Q00301` · Nhóm gốc 1.
