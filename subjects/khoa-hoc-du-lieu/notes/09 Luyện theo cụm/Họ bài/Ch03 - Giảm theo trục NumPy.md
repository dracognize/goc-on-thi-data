# Giảm theo trục NumPy

**Quy tắc nhận diện và giải.** Gọi tên trục bị bỏ, xác định shape còn lại, rồi diễn giải giá trị tương ứng với từng phần tử.

Cần biết trước [Shape axis và broadcasting](../../03%20NumPy%20v%C3%A0%20Pandas/01%20Shape%20axis%20v%C3%A0%20broadcasting.md). Nguồn ScoreUp.

## 1. Cơ bản

Mảng arr có shape (5, 4). Kết quả của arr.sum(axis=1) có shape nào?

- **A.** () — một số vô hướng
- **B.** (4,)
- **C.** (5, 4)
- **D.** (5,)

> **tip** Gợi ý
> Loại đúng chiều ứng với axis.

> **success** Đáp án và hướng giải
> **D.** Shape (5, 4) giảm trên trục 1, còn 5 giá trị với shape (5,).

Mã câu `Q01125` · Nhóm gốc 3.

## 2. Vận dụng

Kết quả của đoạn code sau là gì?
import numpy as np
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(np.sum(arr, axis=0))

- **A.** [4 10 18]
- **B.** [6 15]
- **C.** [5 7 9]
- **D.** [1 2 3]

> **tip** Gợi ý
> Cộng các phần tử cùng cột.

> **success** Đáp án và hướng giải
> **C.** Trục 0 theo chiều các hàng. Lấy 1+4, 2+5, 3+6 thành `[5 7 9]`.

Mã câu `Q01080` · Nhóm gốc 3.

## 3. Tổng hợp

Bảng doanh thu dt có shape (4, 3): bốn chi nhánh theo hàng và ba quý theo cột. Lệnh np.where(dt > 100, 1, 0).sum(axis=1) in ra [3 1 0 2]. Kết luận nào sau đây đúng?

- **A.** Mỗi phần tử là số chi nhánh có doanh thu trên 100 trong một quý; quý đầu tiên có ba chi nhánh vượt 100.
- **B.** Mỗi phần tử là số quý có doanh thu trên 100 của một chi nhánh; chi nhánh đầu tiên vượt 100 ở cả ba quý.
- **C.** Mỗi phần tử là tổng doanh thu của một chi nhánh sau khi bỏ các quý không vượt 100; chi nhánh đầu đạt 3.
- **D.** Mỗi phần tử là số quý bị loại vì không vượt 100 của một chi nhánh; chi nhánh đầu tiên bị loại ba quý.

> **tip** Gợi ý
> Xác định ý nghĩa của 0 và 1 trước khi giải thích tổng.

> **success** Đáp án và hướng giải
> **B.** where cho 1 tại quý doanh thu vượt 100. Sum trục 1 đếm quý theo chi nhánh, nên chi nhánh đầu có cả ba quý vượt ngưỡng.

Mã câu `Q01017` · Nhóm gốc 3.
