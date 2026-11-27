# Trace range vòng lặp và tích lũy

**Quy tắc nhận diện và giải.** Liệt kê lượt chạy, ghi điều kiện và giá trị tích lũy trước/sau mỗi lượt.

Cần biết trước [Điều khiển và hàm](../../02%20Python/07%20%C4%90i%E1%BB%81u%20khi%E1%BB%83n%20v%C3%A0%20h%C3%A0m.md). Nguồn ScoreUp.

## 1. Cơ bản

Giá trị của len(range(2, 11, 3)) là bao nhiêu?

- **A.** 9
- **B.** 3
- **C.** 4
- **D.** 2

> **tip** Gợi ý
> Liệt kê các số từ 2, tiến 3 mỗi lần và dừng trước 11.

> **success** Đáp án và hướng giải
> **B.** Dãy 2, 5, 8 có ba phần tử. Giá trị 11 là mốc loại.

Mã câu `Q00615` · Nhóm gốc 2.

## 2. Vận dụng

Biểu thức [i * 2 for i in range(5) if i % 2 == 1] tạo ra danh sách nào?

- **A.** [0, 4, 8]
- **B.** [1, 3]
- **C.** [2, 6]
- **D.** [0, 2, 4, 6, 8]

> **tip** Gợi ý
> Liệt kê range rồi lọc trước khi nhân.

> **success** Đáp án và hướng giải
> **C.** Trong 0 đến 4 có 1 và 3 thỏa điều kiện lẻ. Nhân đôi được `[2, 6]`.

Mã câu `Q00483` · Nhóm gốc 2.

## 3. Tổng hợp

Một chương trình tính n! bằng: kq = 0; for i in range(1, n + 1): kq *= i; print(kq). Với n = 5, chương trình in ra kết quả nào?

- **A.** 120
- **B.** 5
- **C.** 24
- **D.** 0

> **tip** Gợi ý
> Bắt đầu bảng trace từ giá trị kq trước vòng lặp.

> **success** Đáp án và hướng giải
> **D.** kq khởi tạo 0. Mỗi phép nhân giữ kq bằng 0. Để tính tích, khởi tạo bằng 1.

Mã câu `Q00665` · Nhóm gốc 2.
