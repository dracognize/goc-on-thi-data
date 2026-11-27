# Phương thức list

> **abstract** Tóm tắt
> - List (danh sách) là kiểu **linh hoạt nhất** trong các kiểu hỗn hợp: phần tử cách nhau bằng dấu phẩy, đặt trong `[]`, **khác kiểu cũng được**.
> - Giống mảng trong C nhưng phần tử có thể thuộc nhiều kiểu. List **sửa được** (mutable).
> - Thêm: *`append`*, **`insert`**, **`extend`**. Xóa: **`remove`**, **`pop`**, `del`, **`clear`**. Sắp xếp: *`sort`*, *`reverse`*. Sao chép: **`copy()`**, **`list()`**.
> - Các phương thức sửa list tại chỗ **trả về `None`**.
> - Ma trận biểu diễn bằng **list lồng** (nested list).

**Câu hỏi trước mỗi dòng code.** Đối tượng nào bị sửa? Có tên khác cùng trỏ vào nó không? Lời gọi trả về dữ liệu hay `None`?

## 1. Khái niệm và truy cập

Nguồn tr. 68, tr. 69.

Truy cập bằng toán tử slice `[]` và `[:]` với chỉ số: `0` là phần tử đầu, chỉ số âm đếm từ cuối (`-1` cuối cùng, `-2` áp chót…).

```python
thislist = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]
print(thislist[1])      # banana
print(thislist[-1])     # mango
print(thislist[-4:-1])  # ['orange', 'kiwi', 'melon'] · từ -4 (gồm) đến -1 (không gồm)
print(thislist[2:5])    # ['cherry', 'orange', 'kiwi']
print(thislist[:4])     # ['apple', 'banana', 'cherry', 'orange']
print(thislist[2:])     # ['cherry', 'orange', 'kiwi', 'melon', 'mango']
```

> **warning** Dễ nhầm
> `thislist[1]` trả **một phần tử** (`'banana'`), còn `thislist[1:2]` trả **list** (`['banana']`).

## 2. Cập nhật phần tử

Nguồn tr. 70.

Đặt phần tử (hoặc lát cắt) cần cập nhật **bên trái** dấu gán.

```python
lista = ['physics', 'chemistry', 1997, 2000]
lista[2] = 2001
print(lista)   # ['physics', 'chemistry', 2001, 2000]

listb = ["apple", "banana", "cherry", "orange", "kiwi", "mango"]
listb[1:3] = ["blackcurrant", "watermelon"]
print(listb)   # ['apple', 'blackcurrant', 'watermelon', 'orange', 'kiwi', 'mango']

listc = ["apple", "banana", "cherry"]
listc[1:2] = ["blackcurrant", "watermelon"]   # thay 1 phần tử bằng 2
print(listc)   # ['apple', 'blackcurrant', 'watermelon', 'cherry']

listd = ["apple", "banana", "cherry"]
listd[1:3] = ["watermelon"]                   # thay 2 phần tử bằng 1
print(listd)   # ['apple', 'watermelon']
```

> **tip** Mẹo thi
> Gán vào **slice** thì độ dài list có thể **đổi** (nhiều thay ít, ít thay nhiều). Gán vào **một chỉ số** thì độ dài giữ nguyên.

## 3. Thêm phần tử

Nguồn tr. 71, tr. 72.



> **note** Bảng dạng chữ
> | Phương thức | Làm gì |
> | --- | --- |
> | **`append(x)`** | Thêm *`x`* vào **cuối** (x là một phần tử, kể cả khi x là list) |
> | **`insert(i, x)`** | Chèn *`x`* **tại chỉ số** `i` |
> | **`extend(seq)`** | Nối **từng phần tử** của list/tuple vào cuối |

```python
lista = ["apple", "banana", "cherry"]
lista.append("orange");   print(lista)   # ['apple', 'banana', 'cherry', 'orange']
listb = ["apple", "banana", "cherry"]
listb.insert(1, "orange"); print(listb)  # ['apple', 'orange', 'banana', 'cherry']
list1 = ["apple", "banana", "cherry"]
list2 = ["mango", "pineapple", "papaya"]
tuple = ("kiwi", "orange")
list1.extend(list2);  print(list1)  # ['apple', 'banana', 'cherry', 'mango', 'pineapple', 'papaya']
list2.extend(tuple);  print(list2)  # ['mango', 'pineapple', 'papaya', 'kiwi', 'orange']
```

> **warning** Dễ nhầm: append và extend
> `[1].append([2, 3])` → `[1, [2, 3]]` (độ dài 2). `[1].extend([2, 3])` → `[1, 2, 3]` (độ dài 3). **`extend("ab")`** thêm **từng ký tự** `'a'`, `'b'`.

## 4. Xóa phần tử

Nguồn tr. 73, tr. 74, tr. 75.



> **note** Bảng dạng chữ
> | Cách | Xóa theo | Ghi chú |
> | --- | --- | --- |
> | **`remove(x)`** | **Giá trị** | Nhiều giá trị trùng → xóa cái **đầu tiên bên trái**. Không có → `ValueError` |
> | **`pop(i)`** | **Chỉ số** | Không có `i` (mặc định −1) → xóa **cuối**. Trả về phần tử bị xóa |
> | `del lst[i]` | **Chỉ số** (từ khóa, không phải phương thức) | `del lst` không chỉ số → xóa **cả biến** |
> | **`clear()`** | Tất cả | List vẫn còn, chỉ rỗng `[]` |

```python
lista = ["apple", "banana", "cherry"]; lista.remove("banana"); print(lista)  # ['apple', 'cherry']
listb = ["apple", "banana", "cherry"]; listb.pop(1);    print(listb)  # ['apple', 'cherry']
listc = ["apple", "banana", "cherry"]; listc.pop();     print(listc)  # ['apple', 'banana']
listd = ["apple", "banana", "cherry"]; del listd[0];    print(listd)  # ['banana', 'cherry']
list2 = ["apple", "banana", "cherry"]; list2.clear();   print(list2)  # []

list1 = ["apple", "banana", "cherry"]
del list1
print(list1)   # NameError: name 'list1' is not defined

lista = [123, 'xyz', 'zara', 'abc', 123]
lista.remove(123)
print(lista)   # ['xyz', 'zara', 'abc', 123] · chỉ xóa 123 đầu tiên
```



## 5. Sao chép danh sách

Nguồn tr. 76, tr. 77.

`list2 = list1` **không** sao chép: `list2` chỉ là **tham chiếu** tới cùng list, sửa `list1` thì `list2` "tự động cập nhật".

```python
thislist = ["apple", "banana", "cherry"]
mylist = thislist
print(mylist)        # ['apple', 'banana', 'cherry']
thislist[1] = "orange"
print(mylist)        # ['apple', 'orange', 'cherry'] · đổi theo!
```

Cách tạo bản sao thật: **`copy()`** hoặc **`list()`**.

```python
lista = ["apple", "banana", "cherry"]
mylist = lista.copy()
lista[1] = "orange"
print(mylist)        # ['apple', 'banana', 'cherry'] · không đổi

listb = ["apple", "banana", "cherry"]
mylist = list(listb)
listb[1] = "orange"
print(mylist)        # ['apple', 'banana', 'cherry']
```



> **info** Mở rộng: bản sao nông
> **`copy()`**, **`list()`** và `a[:]` là **sao chép nông**: list ngoài mới, nhưng list con bên trong vẫn dùng chung. Xem trace ở .

## 6. Sắp xếp và đảo ngược

Nguồn tr. 78, tr. 79.

**`sort()`** sắp theo chữ cái và số, **mặc định tăng dần**. Giảm dần dùng *`reverse=True`*. **`reverse()`** **đảo thứ tự** hiện có (không sắp xếp).

```python
lista = ["orange", "mango", "kiwi", "pineapple", "banana"]
lista.sort();              print(lista)  # ['banana', 'kiwi', 'mango', 'orange', 'pineapple']
listb = ["orange", "mango", "kiwi", "pineapple", "banana"]
listb.sort(reverse=True);  print(listb)  # ['pineapple', 'orange', 'mango', 'kiwi', 'banana']
listc = [100, 50, 65, 82, 23]
listc.sort();              print(listc)  # [23, 50, 65, 82, 100]
listd = [100, 50, 65, 82, 23]
listd.sort(reverse=True);  print(listd)  # [100, 82, 65, 50, 23]

fruits = ['apple', 'banana', 'cherry']
fruits.reverse();  print(fruits)   # ['cherry', 'banana', 'apple']
points = [1, 4, 2, 9, 7, 8, 9, 3, 1]
points.reverse();  print(points)   # [1, 3, 9, 8, 7, 9, 2, 4, 1]
```

> **warning** Dễ nhầm
> - **`reverse()`** **không** sắp giảm dần: `[1, 4, 2]` → `[2, 4, 1]`.
> - `a = a.sort()` làm `a` thành `None`. Muốn giữ list gốc dùng `b = sorted(a)` (hàm, trả list mới).
> - Sắp list có cả số và chuỗi → `TypeError`.

## 7. Toán tử, hàm và phương thức khác

Nguồn tr. 80 → tr. 84.

`+` nối, `*` lặp, đều tạo **list mới**.

```python
list1 = ['abcd', 786, 2.23, 'john', 70.2]
list2 = [123, 'john']
print(list2 * 2)       # [123, 'john', 123, 'john']
print(list1 + list2)   # ['abcd', 786, 2.23, 'john', 70.2, 123, 'john']
```



> **note** Bảng dạng chữ
> | Hàm/phương thức | Trả về | Ghi chú |
> | --- | --- | --- |
> | **`len(list)`** | Số phần tử | |
> | **`max(list)`** / **`min(list)`** | Lớn nhất / nhỏ nhất | List **lẫn kiểu** (số và chuỗi) → `TypeError` |
> | **`list(seq)`** | Đổi tuple (hoặc iterable) thành list | |
> | **`list.count(value)`** | Số lần `value` xuất hiện | |
> | **`list.index(elmnt)`** | Vị trí xuất hiện **đầu tiên** | Không có → exception `ValueError` |

```python
fruits = ['apple', 'banana', 'cherry']
print(len(fruits), min(fruits), max(fruits))   # 3 apple cherry
list1 = [10, 30, 20, 40]
print(len(list1), min(list1), max(list1))      # 4 10 40
list2 = [30, 'apple', 'banana', 40]
print(len(list2))   # 4
print(min(list2))   # TypeError: '<' not supported between instances of 'str' and 'int'

print(fruits.count("cherry"))                    # 1
print([1, 4, 2, 9, 7, 8, 9, 3, 1].count(9))      # 2
print(fruits.index("cherry"))                    # 2
print([4, 55, 64, 32, 16, 32].index(32))         # 3 · chỉ lần đầu
```

> **tip** Mẹo thi
> **`max(['apple','banana','cherry'])`** so sánh **theo thứ tự từ điển** → `'cherry'`. **`len()`** vẫn chạy với list lẫn kiểu, chỉ `max/min` lỗi.

## 8. Ma trận bằng nested list

Nguồn tr. 85 → tr. 88.

Ma trận là cấu trúc 2 chiều gồm hàng và cột (ví dụ 3×4: 3 hàng, 4 cột). Python **không có kiểu ma trận riêng**, nên dùng **nested list**: list có phần tử là list.

```python
A = [1, 4, 5, [8, 9]]
print(A[3])          # [8, 9]

A = [[1, 4, 5, 12],
     [-5, 8, 9, 0],
     [-6, 7, 11, 19]]
print("A =", A)
print("A[1] =", A[1])          # [-5, 8, 9, 0]   · hàng thứ 2
print("A[1][2] =", A[1][2])    # 9               · phần tử thứ 3 của hàng thứ 2
print("A[0][-1] =", A[0][-1])  # 12              · phần tử cuối của hàng 1
column = []
for row in A:
    column.append(row[2])
print("Cột thứ 3 =", column)   # [5, 9, 11]
```

$$A = \begin{bmatrix} 1 & 4 & 5 & 12 \\ -5 & 8 & 9 & 0 \\ -6 & 7 & 11 & 19 \end{bmatrix}, \quad A[i][j] = \text{hàng } i, \text{ cột } j \ (\text{đếm từ } 0)$$

**Nhập ma trận m×n từ bàn phím** (tr. 88):

```python
m = int(input("Nhap m = "))
n = int(input("Nhap n = "))
a = []
for i in range(0, m):
    a.append([])                  # tạo hàng rỗng
    for j in range(0, n):
        x = float(input("Nhap phan tu thu a[%2d][%2d]: " % (i+1, j+1)))
        a[i].append(x)            # thêm vào hàng i
print("Day so vua nhap la: ")
for i in range(0, m):
    for j in range(0, n):
        print("%3d " % a[i][j], end='')
    print()                       # xuống dòng sau mỗi hàng
```

> **warning** Dễ nhầm
> Tạo ma trận bằng `[[0]*3]*2` làm **hai hàng cùng một list**: sửa `a[0][0]` thì `a[1][0]` cũng đổi. Dùng vòng lặp như trên hoặc `[[0]*3 for _ in range(2)]`.

## 9. Trace tham chiếu và giá trị trả về



```python
a = [[1], [2]]
alias = a
copy = a.copy()
result = a.append([3])
last = alias.pop()
copy[0].append(9)
```

| Biến | Kết quả | Lý do |
| --- | --- | --- |
| `result` | `None` | append sửa list, trả None |
| `last` | `[3]` | pop lấy phần tử vừa thêm |
| `a`, `alias`, *`copy`* | Đều `[[1, 9], [2]]` | List ngoài của *`copy`* khác, nhưng phần tử con dùng chung |

```python
a = [0]
a.append([3, 4])        # [0, [3, 4]]
a.extend("ab")          # [0, [3, 4], 'a', 'b']
a.insert(-100, "đầu")   # chỉ số quá nhỏ → chèn vào đầu
last = a.pop()          # last == 'b'
a.remove("a")           # a == ['đầu', 0, [3, 4]]
```

> **question** Tự kiểm tra
> 1. `x = [1, 2, 3]; x[1:2] = [7, 8, 9]; print(x)` → `[1, 7, 8, 9, 3]`.
> 2. `x = [1, 2]; y = x.append(3); print(y)` → `None`.
> 3. `x = [3, 1, 2]; x.reverse(); print(x)` → `[2, 1, 3]`.
> 4. `x = [1, 2, 1, 2]; x.remove(2); print(x)` → `[1, 1, 2]`.
> 5. `x = [5, 6, 7]; print(x.pop(), x)` → `7 [5, 6]`.
> 6. `a = [1]; b = list(a); a.append(2); print(b)` → `[1]`.
> 7. `M = [[1, 2], [3, 4]]; print(M[1][0] + M[0][-1])` → `3 + 2 = 5`.
> 8. **`min([3, 'a'])`** → `TypeError`.

**Áp dụng ở** F206 Theo dấu thay đổi của list và tham chiếu · F204 Chỉ số và cắt lát chuỗi-list · F213 List comprehension và biểu thức gọn.

Đối chiếu [tài liệu Python về list](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists).
