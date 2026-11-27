# Cú pháp nhanh · Chương 02

> **abstract** Tóm tắt
> Bảng tra một dòng cho từng cú pháp của Lec 2. Bấm link trang để xem slide gốc.

| Thao tác | Cú pháp | Kiểm tra / bẫy | Slide |
| --- | --- | --- | --- |
| Chú thích | `# một dòng`, `"""nhiều dòng"""` | Ba nháy gán vào biến là chuỗi | tr. 7 |
| Gán nhiều biến | `a = b = c = 10`; `x, y = 1, 2` | Số tên = số giá trị | tr. 12 |
| Chia sàn và dư | `q = a // b`, `r = a % b` | $a = bq + r$; `/` luôn ra float | tr. 15 |
| Gán kết hợp | `b += a`, `b **= a` | Sau `/=` biến thành float | tr. 16 |
| Nhận dạng | `x is y`, `x is not y` | So danh tính, khác `==` | tr. 19 |
| Bit | `&`, `\|`, `^`, `~`, `<<`, `>>` | `~x = -x-1`; `x << n = x·2^n` | tr. 21 |
| In | **`print(*obj, sep=' ', end='\n')`** | `print` trả `None` | tr. 26 |
| Định dạng | `"{} {1} {ten}".format(...)`, `f"{x+y}"`, `"%3.2f" % x` | `{0}` theo vị trí | tr. 28 |
| Nhập | `x = int(input("..."))` | **`input`** luôn trả `str` | tr. 35 |
| Literal số | `0b10011`, `0o17`, `0x12a`, `2+3j` | In ra hệ 10 | tr. 41 |
| Cắt dãy | `xs[start:stop:step]` | stop bị loại; `[::-1]` đảo | tr. 48 |
| Tìm trong chuỗi | **`s.find(x)`**, **`s.index(x)`** | find → −1, index → ValueError | tr. 53 |
| Thêm vào list | **`append(a)`**, **`insert(i, a)`**, **`extend(seq)`** | append thêm 1 phần tử | tr. 71 |
| Xóa trong list | **`remove(v)`**, **`pop(i)`**, `del a[i]`, **`clear()`** | remove theo giá trị | tr. 73 |
| Sao chép | `b = a.copy()`, **`list(a)`**, **`dict(d)`** | `b = a` chỉ là tham chiếu | tr. 76 |
| Tuple 1 phần tử | `(50,)` | `(50)` là int | tr. 94 |
| Set rỗng | **`set()`** | `{}` là dict | tr. 102 |
| Đọc dict có mặc định | **`d.get(k, default)`** | Không chèn khóa mới | tr. 133 |
| Chèn nếu thiếu | **`d.setdefault(k, v)`** | Có khóa thì giữ nguyên | tr. 134 |
| Tạo dict từ 2 dãy | **`dict(zip(l1, l2))`** | Dừng ở dãy ngắn | tr. 131 |
| Rẽ nhánh gọn | **`print("A") if a > b else print("B")`** | | tr. 143 |
| Dãy số | **`range(start, end, step)`** | end bị loại; mặc định 0 và 1 | tr. 150 |
| List comprehension | `[x**2 for x in xs if x > 0]` | for → if → biểu thức | tr. 159 |
| Hàm | `def f(a, b=2): return a*b` | Không return → `None` | tr. 170 |
| Hàm ngắn | `lambda x: x**2` | Thân là một biểu thức | tr. 176 |

Quay lại Mục lục chương 2.
