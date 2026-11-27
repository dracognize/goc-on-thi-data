# Chương 02 · Python

> **abstract** Trang vào chương
> Lec 2 có 178 trang, gồm 5 phần: 2.1 Giới thiệu Python · 2.2 Vào/ra · 2.3 Kiểu dữ liệu · 2.4 Cấu trúc điều khiển · 2.5 Hàm. Mọi trang có nội dung đều được phủ trong bảng . Nguồn Lec 2 · Mục lục slide.

## Thứ tự đọc

1. [01 Biến kiểu dữ liệu và tham chiếu](01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md) · cú pháp, biến, kiểu số và bool, chuyển kiểu, tham chiếu.
2. [03 Biểu thức và vào ra](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) · 8 nhóm toán tử, print, format, f-string, input.
3. [05 Phương thức string](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) · slice và toàn bộ phương thức chuỗi trong slide.
4. [04 Phương thức list](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) · thêm, xóa, sao chép, sắp xếp, ma trận.
5. [06 Phương thức dict set và tuple](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) · tuple, set, dict và phép toán tập hợp.
6. [07 Điều khiển và hàm](07%20%C4%90i%E1%BB%81u%20khi%E1%BB%83n%20v%C3%A0%20h%C3%A0m.md) · if, for, while, list comprehension, def, lambda.
7. [08 Cú pháp nhanh](08%20C%C3%BA%20ph%C3%A1p%20nhanh.md) → [09 Tự kiểm tra](09%20T%E1%BB%B1%20ki%E1%BB%83m%20tra.md) → Thẻ nhớ chương 2.

## Bản đồ chương



## Sơ đồ cần xem

| Sơ đồ | Trả lời câu hỏi |
| --- | --- |
| [02 Tham chiếu và sao chép.excalidraw](../../diagrams/02%20Python/02%20Tham%20chi%E1%BA%BFu%20v%C3%A0%20sao%20ch%C3%A9p.excalidraw.md) | `b = a` và `a[:]` khác nhau thế nào? |
| [Chọn kiểu dữ liệu.excalidraw](../../diagrams/02%20Python/Ch%E1%BB%8Dn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u.excalidraw.md) | Khi nào dùng list, tuple, set, dict, str? |
| [Chỉ số dương và âm của chuỗi.excalidraw](../../diagrams/02%20Python/Ch%E1%BB%89%20s%E1%BB%91%20d%C6%B0%C6%A1ng%20v%C3%A0%20%C3%A2m%20c%E1%BB%A7a%20chu%E1%BB%97i.excalidraw.md) | Ký tự nào ở chỉ số âm, slice dừng ở đâu? |
| [Xóa phần tử trong list set dict.excalidraw](../../diagrams/02%20Python/X%C3%B3a%20ph%E1%BA%A7n%20t%E1%BB%AD%20trong%20list%20set%20dict.excalidraw.md) | Cách xóa nào gây lỗi, trả về gì? |
| [Luồng break continue else.excalidraw](../../diagrams/02%20Python/Lu%E1%BB%93ng%20break%20continue%20else.excalidraw.md) | break, continue, else của vòng lặp đi đâu? |
| [Từ dữ liệu nhập đến kết quả.excalidraw](../../diagrams/02%20Python/T%E1%BB%AB%20d%E1%BB%AF%20li%E1%BB%87u%20nh%E1%BA%ADp%20%C4%91%E1%BA%BFn%20k%E1%BA%BFt%20qu%E1%BA%A3.excalidraw.md) | input → ép kiểu → tính → print |
| [Bảng tra phương thức list.excalidraw](../../diagrams/02%20Python/B%E1%BA%A3ng%20tra%20ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.excalidraw.md) | Phương thức list nào sửa tại chỗ, trả gì? |

## Phủ slide

| Trang | Chủ đề | Note |
| --- | --- | --- |
| 1–3 | Bìa và mục lục (không có nội dung thi) | — |
| 4–5 | Lịch sử Python | [01 · 1. Lịch sử và đặc điểm Python](01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md) |
| 6–9 | Cú pháp: từ khóa, chú thích, nháy, thụt lề | [01 · 2. Cú pháp cơ bản](01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md) |
| 10–12 | Biến, phép gán, gán liên tiếp | [01 · 3. Biến](01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md) |
| 13–14 | Biểu thức, 8 nhóm toán tử | [03 · 1. Biểu thức và các nhóm toán tử](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 15 | Toán tử số học | [03 · 2. Toán tử số học](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 16 | Toán tử gán | [03 · 3. Toán tử gán](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 17 | So sánh | [03 · 4. Toán tử so sánh](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 18 | Logic and/or/not | [03 · 5. Toán tử logic](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 19 | Nhận dạng is/is not | [03 · 6. Toán tử nhận dạng is, is not](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 20–22 | Bitwise và dịch bit | [03 · 7. Toán tử bitwise và dịch bit](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 23 | Thành viên in/not in | [03 · 8. Toán tử thành viên in, not in](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 24 | Mục lục phần (không có nội dung thi) | — |
| 25–33 | print, format, ký tự thoát, f-string | [03 · 9. Hàm print()](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 34–37 | input và ép kiểu | [03 · 10. Hàm input()](03%20Bi%E1%BB%83u%20th%E1%BB%A9c%20v%C3%A0%20v%C3%A0o%20ra.md) |
| 38 | Mục lục phần (không có nội dung thi) | — |
| 39 | 7 kiểu dữ liệu chuẩn | [01 · 4. Tổng quan kiểu dữ liệu chuẩn](01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md) |
| 40–43 | Number, bool | [01 · 5. Kiểu số và kiểu logic](01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md) |
| 44–45 | Khai báo chuỗi | [05 · 1. Khai báo chuỗi](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 46–48 | Slice và toán tử chuỗi | [05 · 2. Chỉ số, slice và toán tử chuỗi](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 49–50 | capitalize, swapcase, center, count | [05 · 3. Đổi hoa/thường, căn giữa, đếm](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 51–52 | startswith, endswith, split | [05 · 4. startswith, endswith, split, splitlines](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 53–56 | find, rfind, index, rindex, expandtabs | [05 · 5. Tìm kiếm find, rfind, index, rindex, expandtabs](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 57–59 | Các phương thức is…() | [05 · 6. Kiểm tra dạng chuỗi is…()](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 60–62 | join, ljust, rjust, strip | [05 · 7. Ghép, căn lề, làm sạch](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 63–64 | replace, partition | [05 · 8. replace và partition](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 65–66 | len, chr, ord, int | [05 · 9. Hàm dùng với chuỗi len, chr, ord, int](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 67 | Xóa ký tự, đảo chuỗi | [05 · 10. Hai thủ thuật xóa ký tự và đảo chuỗi](05%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20string.md) |
| 68–69 | List, truy cập | [04 · 1. Khái niệm và truy cập](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 70 | Cập nhật | [04 · 2. Cập nhật phần tử](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 71–72 | append, insert, extend | [04 · 3. Thêm phần tử](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 73–75 | remove, pop, del, clear | [04 · 4. Xóa phần tử](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 76–77 | Sao chép | [04 · 5. Sao chép danh sách](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 78–79 | sort, reverse | [04 · 6. Sắp xếp và đảo ngược](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 80–84 | +, *, len/max/min, count, index | [04 · 7. Toán tử, hàm và phương thức khác](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 85–88 | Ma trận nested list | [04 · 8. Ma trận bằng nested list](04%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20list.md) |
| 89–90 | Tuple: khái niệm | [06 · 1. Khái niệm](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 91–93 | Tuple: toán tử, truy cập | [06 · 2. Toán tử, hàm và truy cập](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 94–97 | Tuple bất biến, cách sửa/thêm/xóa | [06 · 3. Không sửa được và cách lách](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 98–99 | Hàm với tuple | [06 · 4. Hàm với tuple](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 100–102 | Set: khái niệm, khởi tạo | [06 · 5. Khái niệm và khởi tạo](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 103–105 | Set: truy cập, thêm | [06 · 6. Truy cập, thay đổi, thêm](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 106–108 | Set: xóa | [06 · 7. Xóa item](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 109–112 | Phép toán tập hợp | [06 · 8. Phép toán tập hợp](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 113–116 | Dict: khai báo | [06 · 9. Khái niệm và khai báo](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 117–119 | keys, values, items | [06 · 10. Truy cập keys, values, items](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 120–123 | Sửa, thêm item | [06 · 11. Thay đổi và thêm item](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 124–126 | Xóa item dict | [06 · 12. Xóa item](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 127–129 | Sao chép, nested dict | [06 · 13. Sao chép và dict lồng nhau](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 130–132 | len, str, type, zip, sorted | [06 · 14. Hàm với dict len, str, type, del, zip, sorted](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 133–137 | Phương thức dict | [06 · 15. Phương thức của dict](06%20Ph%C6%B0%C6%A1ng%20th%E1%BB%A9c%20dict%20set%20v%C3%A0%20tuple.md) |
| 138–139 | Chuyển đổi kiểu | [01 · 6. Chuyển đổi kiểu dữ liệu](01%20Bi%E1%BA%BFn%20ki%E1%BB%83u%20d%E1%BB%AF%20li%E1%BB%87u%20v%C3%A0%20tham%20chi%E1%BA%BFu.md) |
| 140 | Mục lục phần (không có nội dung thi) | — |
| 141–147 | if, if-else, elif, nested if | [07 · 1. Cấu trúc if](07%20%C4%90i%E1%BB%81u%20khi%E1%BB%83n%20v%C3%A0%20h%C3%A0m.md) |
| 148–158 | for, range, break, continue, pass, else, lồng | [07 · 2. Vòng lặp for](07%20%C4%90i%E1%BB%81u%20khi%E1%BB%83n%20v%C3%A0%20h%C3%A0m.md) |
| 159 | List comprehension | [07 · 2.6 List comprehension](07%20%C4%90i%E1%BB%81u%20khi%E1%BB%83n%20v%C3%A0%20h%C3%A0m.md) |
| 160–167 | while, break, continue, else, ví dụ | [07 · 3. Vòng lặp while](07%20%C4%90i%E1%BB%81u%20khi%E1%BB%83n%20v%C3%A0%20h%C3%A0m.md) |
| 168 | Mục lục phần (không có nội dung thi) | — |
| 169–177 | def, tham số mặc định, giai thừa, lambda | [07 · 4. Hàm](07%20%C4%90i%E1%BB%81u%20khi%E1%BB%83n%20v%C3%A0%20h%C3%A0m.md) |
| 178 | Trang cuối (không có nội dung thi) | — |

**Kiểm tra phủ.** 178/178 trang nằm trong một dải. 7 trang bìa/mục lục/cuối không có nội dung thi (1–3, 24, 38, 140, 168, 178).

## Họ bài tập của chương

Sau phần tự kiểm tra, luyện theo họ. Xem thêm các họ bài của chương 2.

| Họ giải | Note lý thuyết |
| --- | --- |
| F201 Kiểu dữ liệu, literal và ép kiểu | 01 |
| F202 Toán tử số học – chia sàn, phần dư, lũy thừa | 03 |
| F203 Biểu thức so sánh và logic | 03 |
| F204 Chỉ số và cắt lát chuỗi-list | 05 |
| F205 Phương thức chuỗi và định dạng | 05 |
| F206 Theo dấu thay đổi của list và tham chiếu | 04 |
| F207 Dict, set và tuple | 06 |
| F208 Rẽ nhánh if-elif-else | 07 |
| F209 Trace vòng lặp, range và tích lũy | 07 |
| F210 Hàm, tham số, return và lambda | 07 |
| F211 Vào-ra, input và lỗi khi chạy | 03 |
| F212 Notebook, môi trường và thư viện | ngoài slide Lec 2 |
| F213 List comprehension và biểu thức gọn | 07, 04 |

## Tra API và phương thức



**Đầu ra.** Trace được đoạn code chưa gặp, chỉ ra kiểu, đối tượng bị sửa, giá trị trả về và dòng có thể gây lỗi. Đạt ít nhất 12/15 câu [tự kiểm tra](09%20T%E1%BB%B1%20ki%E1%BB%83m%20tra.md) và nhớ ≥ 80% thẻ nhớ. Chuẩn bị cho [Chương 03](../03%20NumPy%20v%C3%A0%20Pandas/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md).

## Phân tích chuyên sâu

So sánh a.sort() và sorted(a) khi b = a, và 'a,,b'.split(',') với split() không đối số.

> **check** Lập luận và ca biên
> Theo dõi ba cột: tên biến, đối tượng, kết quả trả về. a.sort() đổi cả trạng thái nhìn qua b và trả None. sorted(a) tạo list riêng. Dấu phân cách tường minh giữ trường rỗng. split() không đối số chỉ tách cụm khoảng trắng.
