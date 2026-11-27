# Trùng theo khóa và quy tắc giữ dòng

**Lý thuyết.** [Thiếu và trùng](../../05%20L%C3%A0m%20s%E1%BA%A1ch/01%20Thi%E1%BA%BFu%20v%C3%A0%20tr%C3%B9ng.md) · [Bảng tra chương 5](../../05%20L%C3%A0m%20s%E1%BA%A1ch/05%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md)

**Dấu hiệu và hướng giải.** Chọn khóa xác định mục trùng và quy tắc giữ dòng. Tách phép đếm dòng bị lặp khỏi số nhóm có giá trị lặp.

## Ví dụ có lời giải

Ví dụ mới: cột khóa `[A,A,A,B,B,C]`. Mặc định giữ một dòng mỗi nhóm, còn 3. Với `keep=False`, loại cả nhóm A và B, còn duy nhất C.

## Bài luyện từ ScoreUp

Làm theo thứ tự. Viết đáp án và một dòng lý do, sau đó mở gợi ý nếu cần.

### 1 · Cơ bản

Bảng giao dịch có các cột MaKH, MaSP, SoLuong, mỗi khách có thể mua nhiều dòng khác nhau. Biểu thức nào cho biết số khách hàng duy nhất?

- **A.** len(df.drop_duplicates())
- **B.** df.duplicated().sum()
- **C.** len(df.drop_duplicates(subset=['MaKH']))
- **D.** df.drop_duplicates(subset=['MaKH']).shape[1]

> **tip** Gợi ý
> Cần đếm khách duy nhất theo định danh thay vì toàn bộ hàng.

> **success** Đáp án C
> `drop_duplicates(subset=['MaKH'])` giữ một dòng cho mỗi mã rồi lấy `len`.

Nguồn ScoreUp, nhóm 5, ID `Q01938`.

### 2 · Vận dụng

Nhóm làm sạch bảng giao dịch bằng cách giữ lại lần xuất hiện cuối cùng của mỗi KhachHang. Tổng DoanhThu in ra là bao nhiêu?

```python
import pandas as pd

df = pd.DataFrame({
    'KhachHang': ['A', 'B', 'A', 'C', 'B', 'A'],
    'DoanhThu': [5, 7, 5, 9, 8, 6]
})
sach = df.drop_duplicates(subset=['KhachHang'], keep='last')
print(sach['DoanhThu'].sum())
```

- **A.** 21
- **B.** 23
- **C.** 35
- **D.** 9

> **tip** Gợi ý
> Lần xuất hiện cuối của A, B và C mang giá trị nào?

> **success** Đáp án B
> A ở cuối là 6, B ở lần cuối là 8, C là 9. Tổng 23.

Nguồn ScoreUp, nhóm 5, ID `Q01925`.

### 3 · Tổng hợp

Bảng có 800 dòng. drop_duplicates() mặc định còn 750 dòng, trong đó có đúng 20 tổ hợp giá trị xuất hiện từ hai lần trở lên trong bảng gốc. Nếu dùng drop_duplicates(keep=False), bảng còn bao nhiêu dòng?

- **A.** 750 dòng
- **B.** 780 dòng
- **C.** 700 dòng
- **D.** 730 dòng

> **tip** Gợi ý
> Sau khi đã giữ 1 đại diện mỗi tổ hợp, còn bao nhiêu đại diện thuộc nhóm có trùng?

> **success** Đáp án D
> Từ 750 tổ hợp duy nhất, bỏ thêm 20 đại diện nhóm bị trùng. Kết quả 730.

Nguồn ScoreUp, nhóm 5, ID `Q01945`.

## Ôn lại

Đổi một giả định trong bài cuối và dự đoán kết quả trước khi chạy. Ghi câu sai hoặc đúng do đoán vào sổ lỗi để giải lại sau 1, 3 và 7 ngày.
