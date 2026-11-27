# Nhãn và loại bài toán

**Quy tắc nhận diện và giải.** Tìm biến mục tiêu, kiểm tra có nhãn rồi chọn đầu ra số, lớp hay nhóm chưa có tên.

Cần biết trước [Nhãn và loại bài toán](../../01%20T%E1%BB%95ng%20quan/03%20Nh%C3%A3n%20v%C3%A0%20lo%E1%BA%A1i%20b%C3%A0i%20to%C3%A1n.md). Nguồn ScoreUp.

## 1. Cơ bản

Trong học máy có giám sát, 'Label' (nhãn) là gì?

- **A.** Giá trị mục tiêu đúng mà mô hình cần học để dự đoán, như lợi nhuận hay nhãn 'có mua'/'không mua'
- **B.** Tập các cột đặc trưng đầu vào mà mô hình dùng để đưa ra dự đoán, như tuổi hay thu nhập
- **C.** Ghi chú mô tả nguồn gốc và ý nghĩa từng cột trong bộ dữ liệu, như tên cột hay đơn vị đo
- **D.** Công thức toán học mà thuật toán dùng để tính sai số khi huấn luyện, như MSE hay MAE

> **tip** Gợi ý
> Hỏi đại lượng nào mô hình cần học để dự đoán.

> **success** Đáp án và hướng giải
> **A.** Label là giá trị mục tiêu đã biết trong dữ liệu gán nhãn. Nó khác đặc trưng đầu vào, tên thuật toán và số hàng.

Mã câu `Q00095` · Nhóm gốc 1.

## 2. Vận dụng

Xét hai bài toán: (a) dự đoán giá nhà ở Hà Nội từ diện tích, số phòng, vị trí khi đã có giá bán thực tế của hàng nghìn căn; (b) chia khách hàng thành các nhóm có hành vi mua giống nhau khi chưa có nhãn nhóm nào. Cách gán hướng tiếp cận nào đúng?

- **A.** (a) học có giám sát; (b) học không giám sát
- **B.** Cả (a) và (b) đều là học có giám sát
- **C.** Cả (a) và (b) đều là học không giám sát
- **D.** (a) không giám sát; (b) giám sát

> **tip** Gợi ý
> Tách hai tình huống và xác định tình huống nào có giá trị đích.

> **success** Đáp án và hướng giải
> **A.** Giá bán đã biết nên (a) có giám sát, cụ thể là hồi quy. Bài (b) cần tìm nhóm chưa có nhãn nên không giám sát.

Mã câu `Q00045` · Nhóm gốc 1.

## 3. Tổng hợp

Một sinh viên mã hóa setosa = 0, versicolor = 1, virginica = 2, dùng hồi quy tuyến tính để dự đoán con số này rồi làm tròn thành nhãn. Vấn đề cốt lõi của cách làm này là gì?

- **A.** Hồi quy tuyến tính không chạy được khi biến mục tiêu nhận giá trị nguyên, nên phải đổi nhãn sang số thực trước khi huấn luyện
- **B.** Hồi quy ngầm coi nhãn có thứ tự và khoảng cách, và có thể cho giá trị như 1.5 không ứng với loài nào
- **C.** Việc mã hóa làm mất thông tin về tên loài hoa nên mô hình không thể in kết quả dự đoán ra dưới dạng bảng cho người dùng
- **D.** Ba nhãn phải được mã hóa thành 0, 0.5 và 1 thì mô hình hồi quy tuyến tính mới ước lượng được các hệ số

> **tip** Gợi ý
> Thử đổi cách đánh số ba loài. Quan hệ thật giữa các lớp có đổi không?

> **success** Đáp án và hướng giải
> **B.** Nhãn loài chỉ là mã. Hồi quy tuyến tính dùng số như thang có thứ tự và khoảng cách, nên làm tròn dự đoán có thể áp đặt quan hệ giả giữa các lớp.

Mã câu `Q00227` · Nhóm gốc 1.
