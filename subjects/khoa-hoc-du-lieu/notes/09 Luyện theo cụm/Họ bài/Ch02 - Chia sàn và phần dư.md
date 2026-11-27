# Chia sàn và phần dư

**Quy tắc nhận diện và giải.** Viết $a=bq+r$ cho mỗi bước, với $q$ là thương lấy sàn.

Cần biết trước [Biểu thức và vào ra](../../02%20Python/03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md). Nguồn ScoreUp.

## 1. Cơ bản

Biết 47 // 6 cho kết quả 7. Không cần chạy thêm, hãy suy ra giá trị của 47 % 6.

- **A.** 6
- **B.** 7
- **C.** 5
- **D.** 1

> **tip** Gợi ý
> Dùng đẳng thức số bị chia bằng thương nhân số chia cộng phần dư.

> **success** Đáp án và hướng giải
> **C.** Phần dư là $47-6\times7=5$.

Mã câu `Q00517` · Nhóm gốc 2.

## 2. Vận dụng

Trong Python, biểu thức (-7) // 2 và (-7) % 2 lần lượt cho kết quả nào?

- **A.** -3 và -1
- **B.** -4 và -1
- **C.** -4 và 1
- **D.** -3 và 1

> **tip** Gợi ý
> Floor đi về phía âm vô cùng.

> **success** Đáp án và hướng giải
> **C.** Thương $-7/2=-3.5$ lấy sàn thành $-4$. Dư là $-7-2(-4)=1$.

Mã câu `Q00447` · Nhóm gốc 2.

## 3. Tổng hợp

Đoạn code sau đổi một số tiền ra các tờ 500 nghìn, 200 nghìn và phần lẻ. Nó in ra kết quả nào?

```python
tien = 1_235_000
to_500 = tien // 500_000
con_lai = tien % 500_000
to_200 = con_lai // 200_000
con_lai2 = con_lai % 200_000
print(to_500, to_200, con_lai2)
```

- **A.** 2 1 35000
- **B.** 2 1 235000
- **C.** 2 2 35000
- **D.** 2 1 0

> **tip** Gợi ý
> Lấy thương và dư theo từng mệnh giá. Chuyển phần dư sang lượt sau.

> **success** Đáp án và hướng giải
> **A.** 1.235.000 cho 2 tờ 500.000, dư 235.000. Số dư cho 1 tờ 200.000, còn 35.000. Kết quả in là `2 1 35000`.

Mã câu `Q00433` · Nhóm gốc 2.
