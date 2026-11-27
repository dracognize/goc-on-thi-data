# Tự kiểm tra · Chương 03

> **question** Làm nóng · Một mảng có 2 hàng, mỗi hàng 3 cột. Giải thích shape, ndim, size và ô đầu tiên
> Shape `(2, 3)`, ndim `2`, size `6`. Ô đầu tiên dùng `a[0, 0]`, vì vị trí đếm từ 0.

> **question** 1. `np.arange(12).reshape(3, -1)` có shape gì?
> `(3, 4)`. Mỗi hàng có 4 phần tử.

> **question** 2. `a` shape `(5, 3)`. `a.mean(axis=1, keepdims=True)` có shape gì?
> `(5, 1)`. Tính một số cho mỗi hàng và giữ cột độ dài 1.

> **question** 3. `(2, 3)` có cộng trực tiếp với mảng `(2,)` được không?
> Không. Hai chiều cuối 3 và 2 xung đột. Nếu muốn một số mỗi hàng, reshape mảng kia thành `(2, 1)`.

> **question** 4. Sửa `b` sau khi `b = a0, 2` có sửa a?
> Advanced indexing tạo bản sao khi đọc. Sửa b không sửa a.

> **question** 5. Series có index `[20, 10, 30]` và giá trị `[2, 1, 3]`. `s.loc[10]` và `s.iloc[0]` cho gì?
> `1` và `2`. Hai lệnh chọn nhãn 10 và vị trí 0.

> **question** 6. Cộng hai Series có nhãn giống nhau nhưng khác thứ tự. Giá trị khớp theo gì?
> Theo nhãn. Kiểm tra các nhãn chỉ có một bên vì chúng tạo giá trị thiếu với phép cộng thường.

> **question** 7. `np.linspace(0, 10, 5, endpoint=False)`?
> `[0. 2. 4. 6. 8.]`. Bước 10/5 = 2, không lấy 10. Xem [linspace](08%20H%C3%A0m%20t%E1%BA%A1o%20m%E1%BA%A3ng%20v%C3%A0%20dtype.md).

> **question** 8. `np.array([3.7, -2.6]).astype(int)`?
> `[ 3 -2]`. Cắt phần lẻ về phía 0.

> **question** 9. `a = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])`. `a[[0, 1], [3, 0]]`?
> `[4 5]`. Ghép cặp (0, 3) và (1, 0).

> **question** 10. `np.arange(24).reshape(2, 3, 4).T.shape`?
> `(4, 3, 2)`. **`.T`** đảo ngược mọi trục.

> **question** 11. `pd.DataFrame(data, columns=["Tên", "Lớp"])` khi dict không có "Lớp"?
> Cột "Lớp" toàn NaN. Xem [columns](11%20DataFrame%20t%E1%BA%A1o%2C%20truy%20xu%E1%BA%A5t%20v%C3%A0%20c%E1%BA%ADp%20nh%E1%BA%ADt.md).

> **question** 12. `pd.Index(["a", "b"])[0] = "z"` báo gì?
> TypeError, vì Index bất biến. Xem [Index bất biến](04%20Index%20v%C3%A0%20c%C4%83n%20ch%E1%BB%89nh%20Pandas.md).

Đạt khi đúng ít nhất 10/12 và tự diễn giải được chữ axis trong câu 2. Quay lại [Mục lục Chương 03](00%20M%E1%BB%A5c%20l%E1%BB%A5c.md).
