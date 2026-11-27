# Shape, axis và broadcasting

> **abstract** Tóm tắt
> **shape** là tuple ghi độ dài từng chiều. **`reshape`** đổi cách nhóm nhưng **giữ nguyên số phần tử**, cho phép một chiều `-1`. Chuyển vị **`.T`** đảo thứ tự trục. **Broadcasting** so shape từ phải sang trái: mỗi cặp phải bằng nhau hoặc có một bên bằng 1.

Cần biết trước [quy ước axis](07%20Gi%E1%BB%9Bi%20thi%E1%BB%87u%20NumPy%20v%C3%A0%20ndarray.md).

## Shape của mảng

Nguồn tr. 32.

**Hình dạng** (shape) là kích thước của mỗi chiều. Đọc bằng thuộc tính **`.shape`** hoặc hàm **`np.shape()`**, kết quả là một tuple.

```python
arr1 = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(arr1.shape)        # (2, 4)    2 hàng, 4 cột
arr2 = np.array([1, 2, 3, 4], ndmin=5)
print(np.shape(arr2))    # (1, 1, 1, 1, 4)
```

`ndim` = số phần tử của tuple shape. *`size`* = tích các số trong shape (Mở rộng: `arr1.size` → 8).

## Reshape: đổi hình dạng, giữ số phần tử

Nguồn tr. 33, tr. 34, tr. 35, tr. 36.

Dùng phương thức **`a.reshape(...)`** hoặc hàm **`np.reshape(a, ...)`**. Phần tử được rải lại **theo thứ tự hàng** (đọc trái sang phải, trên xuống dưới).

```python
arr1 = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
print(np.reshape(arr1, (4, 3)))
# [[ 1  2  3]
#  [ 4  5  6]
#  [ 7  8  9]
#  [10 11 12]]
print(np.reshape(arr1, (2, 3, 2)))
# [[[ 1  2]
#   [ 3  4]
#   [ 5  6]]
#
#  [[ 7  8]
#   [ 9 10]
#   [11 12]]]
```

**Có reshape với mọi kích thước được không?** Không. Tích các chiều mới phải bằng số phần tử.

```python
np.array([1, 2, 3, 4, 5, 6, 7, 8]).reshape(3, 3)
# ValueError: cannot reshape array of size 8 into shape (3,3)
```

**Chiều "không xác định" `-1`.** Truyền `-1` cho đúng một chiều, NumPy tự tính.

```python
arr1 = np.array([1, 2, 3, 4, 5, 6, 7, 8])
print(arr1.reshape(2, 2, -1))   # -1 = 8 / (2*2) = 2
# [[[1 2]
#   [3 4]]
#
#  [[5 6]
#   [7 8]]]
print(np.array([[1, 2, 3], [4, 5, 6]]).reshape(-1))   # [1 2 3 4 5 6]  làm phẳng
```

> **example** Ví dụ: tính chiều `-1` từng bước
> **`np.arange(24).reshape(3, -1, 2)`** → size 24, các chiều biết là 3 × 2 = 6 → chiều thiếu = 24 / 6 = **4** → shape `(3, 4, 2)`.

> **warning** Dễ nhầm
> Chỉ được **một** `-1`. **`reshape(-1, -1)`** báo lỗi. **`reshape(-1)`** luôn cho mảng 1D.

## Chuyển vị và hoán đổi trục

Nguồn tr. 37, tr. 38, tr. 39.

Với mảng 2D, **chuyển vị** (transpose) đổi hàng thành cột, tức hoán đổi trục 0 và 1. Dùng `arr.T` hoặc **`np.transpose(arr)`**.

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.T)
# [[1 4]
#  [2 5]
#  [3 6]]
```

Với mảng ≥ 3D, đổi thứ tự trục rất hay dùng trong xử lý ảnh, tensor deep learning:

```python
arr3d = np.arange(24).reshape(2, 3, 4)
print(arr3d.shape)                            # (2, 3, 4)
print(np.transpose(arr3d, (1, 0, 2)).shape)   # (3, 2, 4)   trục mới = (trục1, trục0, trục2)
print(arr3d.T.shape)                          # (4, 3, 2)   đảo ngược toàn bộ
print(np.swapaxes(arr3d, 0, 2).shape)         # (4, 3, 2)   đổi chỗ trục 0 và 2
```



> **note** Bảng dạng chữ
> | Cách viết | Tác dụng | Shape `(2, 3, 4)` thành |
> | --- | --- | --- |
> | **`.T`** | Đảo ngược thứ tự **mọi** trục | `(4, 3, 2)` |
> | **`np.transpose(a, axes)`** / **`a.transpose(axes)`** | Xếp trục theo thứ tự tùy ý | *`axes=(1, 0, 2)`* → `(3, 2, 4)` |
> | **`np.swapaxes(a, i, j)`** | Đổi chỗ đúng **2** trục | `(0, 2)` → `(4, 3, 2)` |

> **tip** Mẹo thi
> Với **`transpose(a, (p, q, r))`**: shape mới = `(shape[p], shape[q], shape[r])`. Chỉ cần tra chỉ số, không cần hình dung không gian.

## Broadcasting: quy tắc

Nguồn tr. 52, tr. 53.

**Broadcasting** (lan truyền) tự động "kéo giãn" mảng nhỏ cho khớp mảng lớn để tính theo từng phần tử (element-wise).



> **note** Bảng dạng chữ
> | Đặc điểm | Nội dung |
> | --- | --- |
> | Mục đích | Tính giữa các mảng có kích thước khác nhau |
> | Quy tắc chính | So từng chiều **từ phải sang trái**. Cùng size hoặc có một bên bằng 1 thì broadcast được |
> | Lỗi thường gặp | `ValueError: operands could not be broadcast together` |
> | Cách kiểm soát | **`np.newaxis`**, **`reshape`**, `expand_dims` để đổi shape |
> | Hiệu suất | Rất nhanh vì vector hóa trong C |



Hình tr. 53 có 3 ca, đều cho kết quả shape `(4, 3)`:

| Ca | Mảng trái | Mảng phải | Cách kéo giãn |
| --- | --- | --- | --- |
| 1 | `(4, 3)` | `(4, 3)` | Không cần, cộng từng ô |
| 2 | `(4, 3)` | `(3,)` | Hàng `[0 1 2]` được chép xuống 4 hàng |
| 3 | `(4, 1)` = `[[0],[10],[20],[30]]` | `(3,)` | Cột chép sang 3 cột, hàng chép xuống 4 hàng |

```python
print(np.array([[0], [10], [20], [30]]) + np.array([0, 1, 2]))
# [[ 0  1  2]
#  [10 11 12]
#  [20 21 22]
#  [30 31 32]]
```

## Broadcasting: ví dụ và ca lỗi

Nguồn tr. 54, tr. 55, tr. 56.

```python
a = np.array([1, 2, 3, 4]); b = np.array([10, 20, 30, 40])
print(a * b)                  # [ 10  40  90 160]      (4,) * (4,)
a = np.array([[1, 2, 3, 4], [1, 2, 3, 4]])
print(a * b)                  # [[ 10  40  90 160]
                              #  [ 10  40  90 160]]    (2,4) * (4,)
a = np.array([[0., 0, 0], [10, 10, 10], [20, 20, 20], [30, 30, 30]])
print(a + np.array([1., 2, 3]))
# [[ 1.  2.  3.]
#  [11. 12. 13.]
#  [21. 22. 23.]
#  [31. 32. 33.]]
```

Hai ca lỗi trong slide:

```python
np.array([[1, 2, 3], [4, 5, 6]]) + np.array([10, 20])
# ValueError: operands could not be broadcast together with shapes (2,3) (2,)
np.array([[1, 2], [3, 4]]) + np.array([5, 6, 7])
# ValueError: operands could not be broadcast together with shapes (2,2) (3,)
```

Ca 1: chiều cuối của a là 3, của b là 2 → khác nhau, không bên nào bằng 1 → lỗi.

> **example** Sửa ca lỗi bằng reshape
> Muốn cộng 10 vào hàng 0 và 20 vào hàng 1: **`b.reshape(2, 1)`** hoặc `b[:, np.newaxis]` → shape `(2, 1)`. Khi đó `(2, 3) + (2, 1)` → `(2, 3)`: `[[11 12 13] [24 25 26]]`.

> **warning** Dễ nhầm
> Hai mảng **cùng số phần tử** chưa chắc broadcast được, và hai mảng **khác số phần tử** vẫn có thể broadcast. Chỉ quy tắc so từng chiều từ phải mới quyết định.

## Đọc phép giảm theo axis

Phần này nối sang [thống kê theo axis](09%20Th%E1%BB%91ng%20k%C3%AA%2C%20t%E1%BA%ADp%20h%E1%BB%A3p%20v%C3%A0%20%C4%91%E1%BA%A1i%20s%E1%BB%91%20tuy%E1%BA%BFn%20t%C3%ADnh.md).





Với `a = np.array([[1, 2, 3], [4, 5, 6]])`: **`a.sum(axis=0)`** → `[5 7 9]` (xóa trục 0, còn 3 số), **`a.sum(axis=1)`** → `[ 6 15]` (xóa trục 1, còn 2 số).

> **info** Mở rộng
> *`keepdims=True`* giữ trục đã giảm với độ dài 1: `a.sum(axis=1, keepdims=True).shape` → `(2, 1)`. Kết quả này broadcast ngược lại được với `a`, ví dụ `a - a.mean(axis=1, keepdims=True)`.

> **question** Tự kiểm tra
> 1. `np.arange(12).reshape(2, -1, 3).shape`? → `(2, 2, 3)`.
> 2. `np.zeros((2, 3, 4)).T.shape`? → `(4, 3, 2)`.
> 3. `np.transpose(np.zeros((2, 3, 4)), (2, 0, 1)).shape`? → `(4, 2, 3)`.
> 4. `(3, 1) + (1, 4)` cho shape gì? → `(3, 4)`.
> 5. `(5, 4) + (5,)` có được không? → Không: chiều cuối 4 ≠ 5.
> 6. `(8, 1, 6) + (7, 1)`? → `(8, 7, 6)`.

Áp dụng ở F302 Dự đoán shape – reshape, chuyển vị, view và copy, F304 Phép toán theo phần tử, ufunc và broadcasting. Học tiếp [03 Truy cập và phép toán NumPy](03%20Truy%20c%E1%BA%ADp%20v%C3%A0%20ph%C3%A9p%20to%C3%A1n%20NumPy.md).
