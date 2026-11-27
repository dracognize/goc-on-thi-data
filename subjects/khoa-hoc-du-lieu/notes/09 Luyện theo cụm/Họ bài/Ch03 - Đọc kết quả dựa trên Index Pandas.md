# Đọc kết quả dựa trên Index Pandas

**Quy tắc nhận diện và giải.** Xác định thao tác dựa trên nhãn hay vị trí, rồi kiểm tra số kết quả và kiểu trả về.

Cần biết trước [Index và căn chỉnh Pandas](../../03%20NumPy%20v%C3%A0%20Pandas/04%20Index%20v%C3%A0%20c%C4%83n%20ch%E1%BB%89nh%20Pandas.md). Nguồn ScoreUp.

## 1. Cơ bản

Cho Series s có chỉ số nhãn [10, 20, 30, 40, 50]. Phát biểu nào đúng về s.loc[20:40] và s.iloc[1:3]?

- **A.** Cả hai cùng trả về 2 phần tử vì đều là lát cắt từ 20 đến 40
- **B.** s.loc[20:40] báo lỗi vì 20:40 không phải là vị trí hợp lệ
- **C.** s.loc[20:40] trả về 2 phần tử (nhãn 20 và 30), s.iloc[1:3] trả về 3 phần tử (vị trí 1 đến 3)
- **D.** s.loc[20:40] trả về 3 phần tử (gồm cả nhãn 40), s.iloc[1:3] trả về 2 phần tử (loại vị trí 3)

> **tip** Gợi ý
> So sánh mốc cuối theo nhãn với mốc cuối theo vị trí.

> **success** Đáp án và hướng giải
> **D.** loc giữ nhãn 20, 30, 40. iloc lấy vị trí 1 và 2, loại 3.

Mã câu `Q01111` · Nhóm gốc 3.

## 2. Vận dụng

DataFrame df có chỉ số hàng là a, b, c và được gán thêm cột gia từ một Series có các nhãn khác. Đoạn code in ra kết quả nào?

```python
import pandas as pd

df = pd.DataFrame({"sp": ["A", "B", "C"]}, index=["a", "b", "c"])
df["gia"] = pd.Series([10, 20, 30], index=["c", "a", "z"])
print(df["gia"].isna().sum(), len(df), len(df.columns))
```

- **A.** 0 3 2
- **B.** 1 4 2
- **C.** 1 3 2
- **D.** 0 4 2

> **tip** Gợi ý
> Tạo từng cặp nhãn nguồn và giá trị, rồi tìm trong các nhãn đích.

> **success** Đáp án và hướng giải
> **C.** Đích a nhận 20, b thiếu, c nhận 10, z bị bỏ. Có 1 ô thiếu, 3 hàng và 2 cột. In `1 3 2`.

Mã câu `Q01002` · Nhóm gốc 3.

## 3. Tổng hợp

Bảng doanh thu có chỉ số hàng trùng lặp. Các dòng in ra khi chạy đoạn code lần lượt là gì?

```python
import pandas as pd

bang = pd.DataFrame({"doanh_thu": [100, 150, 200], "so_don": [10, 12, 20]},
                    index=["HN", "HCM", "HN"])
print(bang.loc["HN"].shape)
print(bang.loc["HCM"].shape)
```

- **A.** (2,) | (2,)
- **B.** (2, 2) | (1, 2)
- **C.** (2, 2) | (2, 1)
- **D.** (2, 2) | (2,)

> **tip** Gợi ý
> Đếm số hàng khớp mỗi nhãn và xác định kiểu của kết quả.

> **success** Đáp án và hướng giải
> **D.** HN khớp hai hàng nên là DataFrame shape (2, 2). HCM khớp một hàng nên là Series shape (2,).

Mã câu `Q01106` · Nhóm gốc 3.
