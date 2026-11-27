# Ghép theo khóa và kiểm soát số hàng

**Lý thuyết.** [Merge concat và combine_first](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/03%20Merge%20concat%20v%C3%A0%20combine_first.md) · [Bảng tra chương 6](../../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Chỉ rõ bảng trái, bảng phải và khóa. Tách yêu cầu giữ hàng bên nào khỏi kiểm tra bội số khớp mỗi khóa.

## Ví dụ có lời giải

Ví dụ mới: trái có khóa A,A,B, phải có A,A,C. Inner có $2\times2=4$ dòng. Left thêm B nên có 5 dòng, outer thêm cả C nên có 6 dòng.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Trong phân tích kinh doanh, khi nào nên dùng pd.merge thay vì pd.concat?

- **A.** Khi muốn giữ nguyên chỉ số hàng ban đầu của từng bảng và không cần dùng khóa chung nào để ghép các dòng
- **B.** Khi hai bảng có cùng cấu trúc cột và chỉ cần xếp chồng thêm các dòng mới vào phía dưới bảng đầu
- **C.** Khi hai bảng chứa thông tin khác nhau về cùng đối tượng, như khách hàng và đơn hàng, và cần ghép theo khóa chung
- **D.** Khi muốn tạo chỉ số hàng nhiều cấp để đánh dấu xem mỗi dòng đến từ bảng nguồn nào trong số các bảng

> **tip** Gợi ý
> Hai bảng phải ghép hàng tương ứng theo thông tin nào?

> **success** Đáp án C
> Dùng `merge` khi cần kết hợp các cột của cùng đối tượng theo khóa, như mã khách.

Nguồn ScoreUp, nhóm 6, ID `Q02468`.

### 2 · Vận dụng

Bảng orders (nhiều đơn mỗi khách) được gộp với bảng customers, trong đó mỗi khách chỉ được phép có đúng một dòng. Cần pandas báo lỗi nếu customers vô tình có mã khách bị trùng, nhưng vẫn cho phép orders lặp mã. Với pd.merge(orders, customers, on='ma_kh'), nên thêm đối số nào?

- **A.** validate='many_to_one'
- **B.** validate='one_to_many'
- **C.** validate='one_to_one'
- **D.** validate='many_to_many'

> **tip** Gợi ý
> Xét tính duy nhất riêng từng phía và theo đúng thứ tự đối số.

> **success** Đáp án A
> Trái được lặp mã, phải duy nhất, nên dùng `validate='many_to_one'`.

Nguồn ScoreUp, nhóm 6, ID `Q02543`.

### 3 · Tổng hợp

Bảng customers (chỉ số customer_code) bị nhập trùng: chỉ số C002 xuất hiện 2 lần (bản ghi cũ và bản ghi mới), nên có 4 dòng gồm C001, C002, C002, C003. Bảng orders có 4 đơn: 1 đơn của C001, 2 đơn của C002, 1 đơn của C003. Lệnh pd.merge(orders, customers, left_on='customer_code', right_index=True) trả về bao nhiêu dòng?

- **A.** 4 dòng
- **B.** 6 dòng
- **C.** 5 dòng
- **D.** 8 dòng

> **tip** Gợi ý
> Đếm các cặp theo từng mã rồi cộng.

> **success** Đáp án B
> C001 và C003 mỗi mã tạo 1. C002 có 2 đơn nhân 2 bản ghi khách tạo 4. Tổng 6.

Nguồn ScoreUp, nhóm 6, ID `Q02541`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
