# Thống kê, tập hợp và đại số tuyến tính

> **abstract** Tóm tắt
> Phép **tổng hợp** (reduction: **`sum`**, **`mean`**, **`std`**, **`min`**…) gộp nhiều số thành ít số hơn, có thể theo *`axis`*. **`cumsum`**/`cumprod` **không** gộp mà giữ nguyên shape. Mảng bool cộng được (True = 1). **`np.unique`**, **`np.isin`** và họ `*1d` làm phép tập hợp. `*` nhân từng phần tử, còn **`@` / `dot`** nhân ma trận. `numpy.linalg` có **`inv`**, `det`, `solve`…

## Thống kê trên cả mảng

Nguồn tr. 57.

Có thể gọi dạng phương thức **`a.mean()`** hoặc hàm **`np.mean(a)`**.

```python
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a.mean())     # 4.0
print(np.mean(a))   # 4.0
print(a.sum())      # 36
```

## Thống kê theo axis

Nguồn tr. 58.

```python
a = np.array([[1, 2, 3], [4, 5, 6]])
print(a.mean(axis=1))   # [2. 5.]    trung bình từng hàng
print(a.sum(axis=0))    # [5 7 9]    tổng từng cột
```

> **warning** Câu chữ trên slide dễ gây rối
> Slide viết "axis=0: tính trên các hàng (thu gọn cột)". Cách nhớ an toàn: **axis=0 làm biến mất trục hàng** → còn một số **mỗi cột**. axis=1 làm biến mất trục cột → còn một số **mỗi hàng**. Luôn kiểm tra bằng shape: `(2, 3)` → axis=0 cho `(3,)`, axis=1 cho `(2,)`.

## Tích lũy cumsum và cumprod

Nguồn tr. 59.

**`cumsum`** (tổng tích lũy) và `cumprod` (tích tích lũy) **không tổng hợp**. Chúng trả mảng kết quả trung gian, **giữ shape**.

```python
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a.cumsum(axis=0))   # cộng dồn xuống dưới theo cột
# [[ 0  1  2]
#  [ 3  5  7]
#  [ 9 12 15]]
print(a.cumsum(axis=1))   # cộng dồn sang phải theo hàng
# [[ 0  1  3]
#  [ 3  7 12]
#  [ 6 13 21]]
print(a.cumsum())         # không axis: làm phẳng rồi cộng dồn
# [ 0  1  3  6 10 15 21 28 36]
```

> **example** Tính `cumsum(axis=1)` hàng 2 bằng tay
> Hàng `[3, 4, 5]` → `3`, `3+4 = 7`, `7+5 = 12` → `[3 7 12]`.

## Bảng phương thức thống kê

Nguồn tr. 60.



> **note** Bảng dạng chữ
> | Phương thức | Mô tả | Với `b = [3, 1, 4, 1, 5]` |
> | --- | --- | --- |
> | **`sum`** | Tổng mọi phần tử | `14` |
> | **`mean`** | Trung bình số học | `2.8` |
> | **`std`**, `var` | Độ lệch chuẩn, phương sai | `1.6`, `2.56` |
> | **`min`**, **`max`** | Nhỏ nhất, lớn nhất | `1`, `5` |
> | `argmin`, **`argmax`** | **Chỉ số** của phần tử nhỏ nhất/lớn nhất | `1`, `4` |
> | **`cumsum`** | Tổng tích lũy | `[ 3 4 8 9 14]` |
> | `cumprod` | Tích tích lũy | `[ 3 3 12 12 60]` |

Công thức: $\bar{x} = \frac{1}{n}\sum x_i$, $\text{var} = \frac{1}{n}\sum (x_i - \bar{x})^2$, $\text{std} = \sqrt{\text{var}}$.

> **warning** Dễ nhầm
> `argmin` trả **vị trí**, không trả giá trị. Có hai số 1 ở vị trí 1 và 3, `argmin` lấy vị trí **đầu tiên**: `1`. NumPy **`std`** mặc định chia cho $n$ (ddof=0), khác Pandas chia cho $n-1$ (Mở rộng).

## Phương thức cho mảng logical

Nguồn tr. 61, tr. 62.

True đổi thành 1, False thành 0. Vì vậy **`sum`** dùng để **đếm** số giá trị True.

```python
a = np.array([[0, 1, 2], [3, -4, 5], [-6, 7, -8]])
print((a > 0).sum())      # 5   (1, 2, 3, 5, 7)

bools = np.array([False, False, True, False])
print(bools.any())        # True    có ít nhất một True
print(bools.all())        # False   không phải tất cả đều True
```

> **tip** Mẹo thi
> Tỷ lệ phần tử thỏa điều kiện: `(a > 0).mean()` → `5/9`.

## Phép toán tập hợp

Nguồn tr. 63, tr. 64, tr. 65.

```python
names = np.array(["Bob", "Joe", "Will", "Bob", "Will", "Joe", "Joe"])
print(np.unique(names))     # ['Bob' 'Joe' 'Will']   duy nhất VÀ đã sắp xếp
print(np.unique(np.array([3, 3, 3, 2, 2, 1, 1, 4, 4])))   # [1 2 3 4]
a = np.array([6, 0, 0, 3, 2, 5, 6])
print(np.isin(a, [2, 3, 6]))   # [ True False False  True  True False  True]
```



> **note** Bảng dạng chữ
> | Hàm | Kết quả | *`x=[1,2,3,4]`*, *`y=[3,4,5]`* |
> | --- | --- | --- |
> | **`unique(x)`** | Phần tử duy nhất, đã sắp | `[1 2 3 4]` |
> | **`intersect1d(x, y)`** | Giao, đã sắp | `[3 4]` |
> | **`union1d(x, y)`** | Hợp, đã sắp | `[1 2 3 4 5]` |
> | **`in1d(x, y)`** | Mảng bool: mỗi phần tử x có trong y? | `[False False True True]` |
> | **`setdiff1d(x, y)`** | Hiệu: trong x, không trong y | `[1 2]` |
> | **`setxor1d(x, y)`** | Hiệu đối xứng: thuộc đúng một bên | `[1 2 5]` |

> **warning** Phiên bản mới
> **`np.in1d`** đã bị bỏ trong NumPy 2.x (máy chạy thử không còn hàm này). Dùng **`np.isin(x, y)`** cho cùng kết quả. Đề thi theo slide vẫn có thể hỏi `in1d`.

## Nhân ma trận: dot và @

Nguồn tr. 66.

`*` giữa hai mảng 2D là nhân **từng phần tử**. Nhân ma trận dùng **`dot`** hoặc toán tử `@`.

```python
x = np.array([[1., 2., 3.], [4., 5., 6.]])          # (2, 3)
y = np.array([[6., 23.], [-1, 7], [8, 9]])          # (3, 2)
print(x.dot(y))    # [[ 28.  64.]
                   #  [ 67. 181.]]
print(x @ y)       # giống hệt
```

Ô hàng 0, cột 0: $1\cdot 6 + 2\cdot(-1) + 3\cdot 8 = 28$. Điều kiện: số cột của x (3) = số hàng của y (3). Kết quả shape `(2, 2)`.

> **warning** Dễ nhầm
> `x * y` ở đây báo lỗi broadcast vì `(2, 3)` và `(3, 2)` không tương thích. `(m, n) @ (n, p)` → `(m, p)`.

## numpy.linalg

Nguồn tr. 67, tr. 68.

```python
from numpy.linalg import inv, qr
a = np.array([[0, 2, 3], [4, 1, 0], [1, 0, 2]])
m = a.T @ a
print(m)                       # [[17  4  2]
                               #  [ 4  5  6]
                               #  [ 2  6 13]]
print(inv(m).round(4))         # [[ 0.0803 -0.1108  0.0388]
                               #  [-0.1108  0.6011 -0.2604]
                               #  [ 0.0388 -0.2604  0.1911]]
print((m @ inv(m)).round(6))   # ma trận đơn vị 3 x 3
```

| Hàm | Mô tả |
| --- | --- |
| `diag` | Lấy các phần tử đường chéo |
| **`dot`** | Nhân ma trận |
| `trace` | Tổng đường chéo |
| `det` | Định thức |
| `eig` | Trị riêng và vector riêng |
| **`inv`** | Nghịch đảo ma trận vuông |
| `pinv` | Nghịch đảo giả Moore-Penrose |
| `qr` | Phân rã QR |
| `svd` | Phân rã giá trị suy biến (SVD) |
| `solve` | Giải hệ $Ax = b$ |
| `lstsq` | Nghiệm bình phương tối thiểu cho $Ax = b$ |

> **example** Ví dụ nhỏ (đã chạy)
> $A = \begin{pmatrix}2 & 1\\1 & 3\end{pmatrix}$, $b = (3, 5)$: **`np.diag(A)`** → `[2. 3.]`, **`np.trace(A)`** → `5.0`, **`np.linalg.det(A)`** → `5.0` ($2\cdot3 - 1\cdot1$), **`np.linalg.solve(A, b)`** → `[0.8 1.4]`.

> **question** Tự kiểm tra
> 1. **`np.array([[1, 2], [3, 4]]).mean(axis=0)`**? → `[2. 3.]`.
> 2. **`np.array([2, 3, 4]).cumprod()`**? → `[ 2  6 24]`.
> 3. **`np.array([5, 9, 2]).argmax()`**? → `1`.
> 4. `(np.array([1, -1, 2]) > 0).sum()`? → `2`.
> 5. **`np.setdiff1d([5, 1, 3], [3])`**? → `[1 5]` (đã sắp).
> 6. `(2, 3) @ (3, 4)` cho shape? → `(2, 4)`.
> 7. Hàm nào giải hệ $Ax=b$? → **`np.linalg.solve`**.

Áp dụng ở F305 Giảm theo trục và thống kê mảng, F306 Đại số tuyến tính với NumPy. Học tiếp [Thực hành NumPy ufunc tệp và ngẫu nhiên](Th%E1%BB%B1c%20h%C3%A0nh%20NumPy%20ufunc%20t%E1%BB%87p%20v%C3%A0%20ng%E1%BA%ABu%20nhi%C3%AAn.md).
