# Danh mục và mã hóa giá trị thiếu

**Lý thuyết.** [Chuỗi và mã hóa phân loại](../../05%20L%C3%A0m%20s%E1%BA%A1ch/04%20Chu%E1%BB%97i%20v%C3%A0%20m%C3%A3%20h%C3%B3a%20ph%C3%A2n%20lo%E1%BA%A1i.md) · [Bảng tra chương 5](../../05%20L%C3%A0m%20s%E1%BA%A1ch/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Kiểm tra biến danh nghĩa hoặc có thứ tự. Chuẩn hóa các biến thể chữ nếu chúng cùng nghĩa, rồi quyết định cách biểu diễn nhóm thiếu.

## Ví dụ có lời giải

Ví dụ mới: `[' HN ', 'hn', None]` sau `astype('string').str.strip().str.lower()` có một nhóm `hn`. One-hot mặc định cho hàng thiếu toàn 0. Nếu chọn `dummy_na=True`, sẽ có thêm cột cho ô thiếu.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Trong tiền xử lý dữ liệu, với đặc trưng có thứ tự {Low, Medium, High}, phương pháp mã hóa phù hợp nhất cho đặc trưng này là gì?

- **A.** One-hot encoding, vì mỗi mức được tách thành một cột riêng nên mô hình học từng mức độc lập.
- **B.** Ordinal encoding với thứ tự Low < Medium < High, vì thứ bậc của các mức được giữ trong số mã.
- **C.** Binary encoding, vì mã nhị phân của mỗi mức phản ánh đúng khoảng cách giữa các mức thứ bậc.
- **D.** Hash ngẫu nhiên, vì mỗi mức nhận một mã số duy nhất nên không bị nhầm lẫn với mức khác.

> **tip** Gợi ý
> Low, Medium và High có quan hệ đã biết.

> **success** Đáp án B
> Ordinal giữ được thứ bậc `Low < Medium < High`. Chọn ánh xạ tường minh theo ý nghĩa nghiệp vụ.

Nguồn ScoreUp, nhóm 5, ID `Q01912`.

### 2 · Vận dụng

Cột phuong_thuc có giá trị Tien mat, The và một số ô thiếu (NaN). Mặc định get_dummies cho các dòng thiếu toàn 0. Muốn tạo thêm một cột riêng đánh dấu dòng thiếu thì dùng tham số nào?

- **A.** drop_first=True
- **B.** sparse=True
- **C.** dummy_na=True
- **D.** prefix_sep='_na'

> **tip** Gợi ý
> Cần cột báo thiếu riêng trong one-hot.

> **success** Đáp án C
> `dummy_na=True` có nhiệm vụ thêm cột biểu thị giá trị thiếu.

Nguồn ScoreUp, nhóm 5, ID `Q01927`.

### 3 · Tổng hợp

Cột gioi_tinh có các giá trị 'Nam', 'Nữ', 'nam', 'Nữ', 'Nam', 'Nam', None, 'Nữ' vì quên chuẩn hóa chữ hoa/thường. Gọi pd.get_dummies(df['gioi_tinh']) với tham số mặc định, kết quả có đặc điểm nào?

- **A.** Có 4 cột (Nam, Nữ, nam, NaN); hàng chứa None có giá trị True ở cột riêng dành cho giá trị thiếu
- **B.** Có 2 cột (Nam, Nữ) vì pandas tự gộp 'Nam' và 'nam' thành một nhãn; hàng chứa None có mọi cột bằng 0
- **C.** Có 3 cột (Nam, Nữ, nam); hàng chứa None có tất cả các cột bằng 0 (False)
- **D.** Có 3 cột (Nam, Nữ, nam); hàng chứa None gây ValueError vì không có nhãn nào để mã hóa

> **tip** Gợi ý
> So sánh phân biệt chữ hoa với cách xử lý None mặc định.

> **success** Đáp án C
> `Nam`, `Nữ`, `nam` là ba nhãn khác nhau. None tạo hàng được mã hóa toàn 0 với cấu hình trong đề.

Nguồn ScoreUp, nhóm 5, ID `Q01935`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
