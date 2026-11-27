# Dự đoán shape trước và sau biến đổi

**Quy tắc nhận diện và giải.** Ghi shape đầu vào rồi theo dõi từng trục đổi vị trí, giữ lại hoặc được chọn.

Cần biết trước [Shape axis và broadcasting](../../03%20NumPy%20v%C3%A0%20Pandas/01%20Shape%20axis%20v%C3%A0%20broadcasting.md). Nguồn ScoreUp.

## 1. Cơ bản

Cho list lồng nhau ba cấp `[[[1, 2], [3, 4]], [[5, 6], [7, 8]]]`. Sau khi chuyển bằng np.array, mảng thu được có ndim và shape nào?

- **A.** ndim = 3, shape = (2, 2, 2)
- **B.** ndim = 1, shape = (8,)
- **C.** ndim = 3, shape = (4, 2)
- **D.** ndim = 2, shape = (2, 4)

> **tip** Gợi ý
> Đếm số phần tử ở từng lớp lồng nhau.

> **success** Đáp án và hướng giải
> **A.** Hai khối, mỗi khối hai hàng, mỗi hàng hai phần tử. Do đó ndim là 3 và shape (2, 2, 2).

Mã câu `Q00880` · Nhóm gốc 3.

## 2. Vận dụng

Cho arr có shape (2, 3, 4). Gọi arr.transpose() không truyền đối số axes thì kết quả có shape nào?

- **A.** Báo lỗi vì transpose bắt buộc phải truyền vào đối số axes khi gọi.
- **B.** (2, 3, 4), giữ nguyên vì chưa chỉ định axes nào để hoán đổi.
- **C.** (3, 2, 4), vì mặc định chỉ hoán đổi vị trí của hai trục đầu tiên.
- **D.** (4, 3, 2), vì mặc định đảo ngược thứ tự của tất cả các trục.

> **tip** Gợi ý
> Đảo thứ tự các trục 0, 1, 2 khi không truyền axes.

> **success** Đáp án và hướng giải
> **D.** Thứ tự mới là 2, 1, 0. Shape thành (4, 3, 2).

Mã câu `Q00952` · Nhóm gốc 3.

## 3. Tổng hợp

Mảng data có shape (7, 2) và mảng mặt nạ mask có 7 phần tử logical, trong đó đúng 2 phần tử True. Biểu thức data[mask, 1:] có shape là gì?

- **A.** (2, 1)
- **B.** (2,)
- **C.** (7, 1)
- **D.** (1, 2)

> **tip** Gợi ý
> Đếm hàng True và cột còn lại sau lát cắt một cách riêng biệt.

> **success** Đáp án và hướng giải
> **A.** Mặt nạ giữ 2 hàng, lát cắt 1: giữ đúng cột thứ hai dưới dạng một trục độ dài 1. Kết quả shape (2, 1).

Mã câu `Q01003` · Nhóm gốc 3.
