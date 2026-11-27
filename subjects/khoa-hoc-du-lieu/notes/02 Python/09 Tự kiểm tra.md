# Tự kiểm tra · Chương 02

Với mỗi câu, ghi kết quả và lý do trước khi mở đáp án.

> **question** 1. `"12" + "3"` và `int("12") + 3` cho gì?
> Chuỗi `"123"` và số nguyên `15`.

> **question** 2. `[0, 1, 2, 3, 4][1:4:2]`?
> `[1, 3]`. Dừng trước chỉ số 4.

> **question** 3. `a = [1]`, `b = a`, `c = a[:]`, sau đó `a.append(2)`. Giá trị của b và c?
> `b == [1, 2]`, `c == [1]`.

> **question** 4. `sum(range(2, 7, 2))`?
> `2 + 4 + 6 = 12`.

> **question** 5. Điều gì xảy ra khi `{[1, 2]}`?
> `TypeError`. List không hashable nên không thể làm phần tử set.

> **question** 6. Hàm chỉ chứa `print(x)` có giá trị trả về gì?
> `None`. Giá trị được in ra là tác động của lệnh print.

> **question** 7. a = [1], b = a, r = a.extend([2, 3]), x = b.pop(0). a, r và x là gì?
> a là `[2, 3]`, r là `None`, x là 1. Hai biến cùng trỏ vào một list.

> **question** 8. So sánh kết quả của " a,,b ".strip().split(",") với " a   b ".split().
> Kết quả lần lượt là `["a", "", "b"]` và `["a", "b"]`.

> **question** 9. "neu".find("N") và "neu".index("N") cho gì?
> find trả −1. index gây ValueError vì tìm phân biệt hoa/thường.

> **question** 10. Với d = {}, gọi d.get("x", 0), rồi d.setdefault("x", 1). d cuối cùng là gì?
> `{"x": 1}`. get đọc giá trị mặc định, setdefault chèn khi thiếu.

> **question** 11. `print(1, 2, 3, sep="*", end="&")` in gì?
> `1*2*3&`, không xuống dòng (tr. 27).

> **question** 12. `(50)` và `(50,)` có kiểu gì?
> `int` và `tuple` (tr. 94).

> **question** 13. `for x in range(6): if x == 3: break` kèm `else: print("F")`. Có in F không?
> Không. else của vòng bị bỏ qua khi thoát bằng break (tr. 156).

> **question** 14. `{1, 2, 3}.symmetric_difference({2, 3, 4})`?
> `{1, 4}` (tr. 112).

> **question** 15. `60 >> 2` và `~60`?
> `15` và `-61` (tr. 21).

Đạt khi đúng ít nhất 12/15, giải thích được câu 7–9 và 13 và tự sửa một đoạn code nhầm giữa phép sửa tại chỗ và giá trị trả về. Quay lại Mục lục Chương 02.
