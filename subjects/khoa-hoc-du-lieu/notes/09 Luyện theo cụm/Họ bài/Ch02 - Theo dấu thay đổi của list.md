# Theo dấu thay đổi của list

**Quy tắc nhận diện và giải.** Ghi trạng thái list sau mỗi thao tác được thực thi. Kiểm tra tham chiếu và cấu trúc nhánh.

Cần biết trước [Biến kiểu dữ liệu và tham chiếu](../../02%20Python/01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md). Nguồn ScoreUp.

## 1. Cơ bản

Phương thức .append() dùng để làm gì?

- **A.** Thêm một phần tử vào cuối danh sách
- **B.** Xóa phần tử đầu tiên khỏi danh sách
- **C.** Tìm vị trí của phần tử trong danh sách
- **D.** Sắp xếp các phần tử trong danh sách

> **tip** Gợi ý
> Xác định thao tác thêm một đối tượng hay nhiều phần tử.

> **success** Đáp án và hướng giải
> **A.** append đặt đúng một phần tử vào cuối list. Nếu truyền một list, toàn bộ list ấy là một phần tử mới.

Mã câu `Q00455` · Nhóm gốc 2.

## 2. Vận dụng

Đoạn code sau in ra kết quả nào?

```python
a = [1, 2, 3]
b = a
c = a[:]
a.append(4)
print(len(b), len(c))
```

- **A.** 4 3
- **B.** 4 4
- **C.** 3 4
- **D.** 3 3

> **tip** Gợi ý
> Vẽ các biến trỏ tới đối tượng trước khi gọi append.

> **success** Đáp án và hướng giải
> **A.** a và b cùng trỏ list ban đầu, c là list khác do slicing. Gọi append làm a và b dài 4, c vẫn dài 3. In `4 3`.

Mã câu `Q00427` · Nhóm gốc 2.

## 3. Tổng hợp

Khi chạy, đoạn code in ra kết quả nào?

```python
sl = 12
kq = []
if sl % 2 == 0:
    kq.append("chan")
if sl % 3 == 0:
    kq.append("chia3")
elif sl > 10:
    kq.append("lon")
else:
    kq.append("nho")
print(kq)
```

- **A.** ['chan', 'chia3']
- **B.** ['chan']
- **C.** ['chan', 'chia3', 'lon']
- **D.** ['chan', 'lon']

> **tip** Gợi ý
> Đánh dấu mỗi lần append và ghép elif với if cùng mức thụt lề gần nhất.

> **success** Đáp án và hướng giải
> **A.** 12 chẵn nên thêm chan. If thứ hai cũng đúng vì 12 chia hết cho 3, thêm chia3. Elif và else thuộc nhánh thứ hai nên bị bỏ qua. In `['chan', 'chia3']`.

Mã câu `Q00468` · Nhóm gốc 2.
