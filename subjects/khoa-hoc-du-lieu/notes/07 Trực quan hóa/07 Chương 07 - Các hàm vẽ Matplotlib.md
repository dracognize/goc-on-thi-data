# Các hàm vẽ trong Matplotlib · 7.3.3

> **abstract** Tóm tắt
> | Hàm | Vẽ gì | Đầu vào chính |
> | --- | --- | --- |
> | **`plot()`** | Đường (dữ liệu liên tục) | `[x], y, [fmt]` |
> | **`bar()`** | Cột dọc (danh mục) | `x, height, width=0.8` |
> | **`barh()`** | Thanh ngang | `y, width, height=0.8` |
> | **`pie()`** | Tròn, tỷ lệ % | `values, labels, autopct` |
> | **`hist()`** | Phân bố tần suất | `data, bins` |
> | **`scatter()`** | Phân tán, quan hệ 2 biến | `x, y, s, c, marker, cmap, alpha` |
> | **`stackplot()`** | Diện tích xếp chồng | `x, *ys, labels, colors, baseline` |

## Hàm plot()

tr. 75

```python
plt.plot([x], y, [fmt], data=None, **kwargs)
plt.plot([x], y, [fmt], [x2], y2, [fmt2], ..., **kwargs)   # nhiều đường trên 1 hệ trục
```

- *`fmt`*: chuỗi định dạng (format string) quy cách vẽ đường.
- *`data`*: nhãn dữ liệu (đối tượng có chỉ mục theo tên, ví dụ DataFrame, khi đó x, y có thể là tên cột).
- `**kwargs`: các tham số vẽ đường.
- **Trả về một list các đối tượng `Line2D`** (kể cả khi chỉ vẽ một đường).

### Các tham số kiểu đường

tr. 76 · tr. 77 · tr. 78



> **note** Bảng dạng chữ
> | Thuộc tính | Tên đầy đủ | Viết tắt | Giá trị ví dụ |
> | --- | --- | --- | --- |
> | Màu đường | *`color`* | *`c`* | `'red'`, `'#FF5733'`, `'b'` |
> | Kiểu đường | *`linestyle`* | `ls` | `'-'` liền · `'--'` đứt · `'-.'` gạch chấm · `':'` chấm chấm |
> | Độ rộng đường | *`linewidth`* | *`lw`* | `2` |
> | Marker | *`marker`* | — | `'o'` tròn · `'s'` vuông · `'*'` sao |
> | Cỡ marker | `markersize` | `ms` | `10` |
> | Màu trong marker | `markerfacecolor` | `mfc` | `'blue'` |
> | Màu viền marker | `markeredgecolor` | `mec` | `'red'` |

> **info** Mở rộng
> Slide nói *`linewidth`* tính bằng "pixels". Chính xác thì đơn vị là **point** (1/72 inch). Với dpi 72 thì 1 point = 1 pixel. Đề thường chỉ hỏi "độ rộng đường" nên hiểu theo slide là đủ.

### Format string `[color][marker][line]`

tr. 79 · tr. 80 · tr. 81

Cách viết ngắn ghép **màu + marker + kiểu đường** vào một chuỗi.



> **note** Bảng dạng chữ
> | [color] | [marker] | [line] |
> | --- | --- | --- |
> | *`b`* blue · `g` green · `r` red | `o` tròn | `-` liền |
> | *`c`* cyan · `m` magenta · *`y`* yellow | `v` tam giác xuống (`^` lên, `<` trái, `>` phải) | `--` đứt |
> | `k` black · `w` white | `*` sao · `.` chấm · `p` ngũ giác · *`s`* vuông | `-.` gạch chấm |
> | `#rrggbb` (dùng qua `color=`) | ... | `:` chấm chấm |



> **example** Ví dụ · Đọc `'ro--'` từng ký tự
> 1. `r` → màu đỏ.
> 2. `o` → marker tròn tại mỗi điểm.
> 3. `--` → nối bằng nét đứt.
>
> ```python
> lines = plt.plot([1, 2], [3, 4], 'ro--')
> print(lines)                       # [<matplotlib.lines.Line2D object at 0x...>]
> l = lines[0]
> print(l.get_color(), l.get_marker(), l.get_linestyle())   # r o --
> ```

> **example** Ví dụ slide · Ba đường một lệnh (tr. 81)
> ```python
> t = np.arange(0., 5., 0.2)        # 0, 0.2, ..., 4.8 (25 giá trị, không gồm 5)
> plt.plot(t, t, 'r--', t, t**2, 'bs', t, t**3, 'g^')
> ```
> - `t` theo `'r--'`: đường thẳng $y=t$, đỏ, nét đứt.
> - `t**2` theo `'bs'`: chỉ **marker vuông xanh**, **không có đường** (fmt không có phần [line]).
> - `t**3` theo `'g^'`: tam giác xanh lá, không đường.

> **warning** Dễ nhầm
> - Slide 80 ghi "*`b`* – black" là **lỗi gõ**. *`b`* = blue, **`k` = black**.
> - Fmt chỉ có marker (`'bs'`, `'g^'`) → **chỉ vẽ điểm**, không nối. Fmt chỉ có màu (`'r'`) → đường liền mặc định.
> - Thứ tự trong fmt linh hoạt (`'--ro'` cũng được), nhưng slide dạy `[color][marker][line]`.
> - Slide gõ `' g^'` có dấu cách đầu; khi chạy thật nên viết `'g^'`.

## Hàm bar()

tr. 82 · tr. 83 · tr. 84

```python
matplotlib.pyplot.bar(x, height, width=0.8, bottom=None, *, align='center', data=None, **kwargs)
```

Vẽ **cột dọc** cho dữ liệu danh mục hoặc so sánh nhóm. *`width`* mặc định **0.8**. *`bottom`* là đáy cột (dùng để xếp chồng).

```python
x = ['A', 'B', 'C', 'D']
y = [3, 7, 5, 6]
plt.bar(x, y)
plt.title('Bar Plot')
```

Từ dict (tr. 83): vẽ bằng **vị trí số** rồi gắn tên bằng *`xticks`*.

```python
D = {'CNTT': 360, 'Kế toán': 310, 'Kinh tế': 360, 'QTKD': 580, 'Mar': 340, 'BH': 290}
plt.bar(range(len(D)), D.values(), align='center')   # cột tại x = 0..5
plt.xticks(range(len(D)), D.keys())                  # đổi nhãn 0..5 thành tên ngành
plt.title('Chỉ tiêu tuyển sinh')
```

Ghép **hai loạt cột** xen kẽ (tr. 84):

```python
plt.bar([1, 3, 5, 7, 9], [5, 2, 7, 8, 2], label="One")
plt.bar([2, 4, 6, 8, 10], [8, 6, 2, 5, 6], label="Two", color='g')
plt.legend()
plt.xlabel('bar number'); plt.ylabel('bar height'); plt.title('Ghép 2 biểu đồ')
```

Loạt "One" (xanh mặc định) ở x lẻ, "Two" (xanh lá) ở x chẵn. **`legend()`** đọc `label=`.

## Hàm barh()

tr. 85 · tr. 86

```python
matplotlib.pyplot.barh(y, width, height=0.8, left=None, *, align='center', **kwargs)
```



> **note** Bảng dạng chữ
> | **`bar`** (dọc) | **`barh`** (ngang) |
> | --- | --- |
> | *`x`* vị trí | *`y`* vị trí |
> | *`height`* độ dài cột | *`width`* độ dài thanh |
> | *`width=0.8`* độ dày | *`height=0.8`* độ dày |
> | *`bottom`* | *`left`* |
> | Nhãn bằng *`xticks`* | Nhãn bằng *`yticks`* |

```python
D = {"CNTT": 240, 'KHMT': 120, 'CĐS': 60, 'KTPM': 50}
n = len(D)
plt.barh(range(n), D.values(), align='center', label='KhoaCNTT')
plt.yticks(range(n), D.keys())
plt.title("Chỉ tiêu TSinh các ngành")
plt.ylabel('Các ngành đào tạo'); plt.xlabel('Số lượng Tsinh')
plt.legend()
```

> **warning** Dễ nhầm
> Trong **`barh`**, **`width` là độ dài giá trị** và **`height` là độ dày thanh** — ngược trực giác so với **`bar`**. Nhãn danh mục nằm trên **trục y** → dùng *`yticks`*.

## Hàm pie()

tr. 87

```python
d = {'CTTT': 360, 'Kế toán': 310, 'Kinh tế': 360, 'QTKD': 580, 'Mar': 340, 'BH': 290}
plt.pie(d.values(), labels=d.keys(), autopct='%1.1f%%')
plt.axis('equal')      # trục x = trục y → hình tròn không bị méo
```

- *`autopct='%1.1f%%'`*: in phần trăm **1 chữ số thập phân**. `%%` in ra ký tự `%`.
- Tổng = 2240. Kết quả (đã tính): CTTT 16.1% · Kế toán 13.8% · Kinh tế 16.1% · **QTKD 25.9%** · Mar 15.2% · BH 12.9%.
- Pie tự chia mỗi giá trị cho tổng — **không cần** chuẩn hóa trước.

## Hàm hist()

tr. 88 · tr. 89 · tr. 90

Biểu diễn **tần suất** các giá trị: chia trục số thành khoảng, mỗi cột cao bằng số quan sát trong khoảng.

> **example** Ví dụ slide · Chiều cao 250 người
> | Khoảng (cm) | 140–145 | 145–150 | 151–156 | 157–162 | 163–168 | 168–173 | 173–178 | 179–184 | 185–190 | 190–195 |
> | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
> | Số người | 2 | 5 | 15 | 31 | 46 | **53** | 45 | 28 | 21 | 4 |
>
> Tổng = 250. Khoảng đông nhất 168–173 cm. Hình dạng gần **hình chuông**, hơi lệch.

```python
data = [1, 2, 2, 3, 3, 3, 4, 4, 5]
n, bins, patches = plt.hist(data, bins=5)
print(n)      # [1. 2. 3. 2. 1.]
print(bins)   # [1.  1.8 2.6 3.4 4.2 5. ]
```

Từng bước: min = 1, max = 5, chia 5 khoảng đều độ rộng $\frac{5-1}{5} = 0.8$. Khoảng cuối **gồm cả 5**. Đếm: {1}, {2,2}, {3,3,3}, {4,4}, {5} → `[1, 2, 3, 2, 1]`.

> **warning** Dễ nhầm
> *`bins=5`* là **số khoảng** (biên do thư viện tính từ min–max). *`bins=[0, 15, 30]`* là **danh sách biên**. **`plt.hist`** trả về bộ ba `(n, bins, patches)`; `len(bins) = số khoảng + 1`.

## Hàm scatter()

tr. 91 · tr. 92 · tr. 93

```python
matplotlib.pyplot.scatter(x, y, s=None, c=None, marker=None, cmap=None, norm=None,
    vmin=None, vmax=None, alpha=None, linewidths=None, *, edgecolors=None,
    plotnonfinite=False, data=None, **kwargs)
```



> **note** Bảng dạng chữ
> | Tham số | Ý nghĩa |
> | --- | --- |
> | *`s`* | **Kích thước** điểm (có thể là mảng → bubble chart) |
> | *`c`* | **Màu** (một màu, hoặc mảng màu/số cho từng điểm) |
> | *`marker`* | Hình dạng điểm |
> | *`cmap`*, *`norm`*, *`vmin`*, *`vmax`* | Bảng màu và chuẩn hóa khi *`c`* là số |
> | *`alpha`* | Độ trong suốt 0–1 |
> | *`linewidths`*, *`edgecolors`* | Viền điểm |

Cần **hai mảng cùng độ dài**: một cho x, một cho y. Ví dụ tr. 92: `x = [1,2,3,4,5]`, `y = [5,7,8,5,6]` → 5 chấm tại (1,5), (2,7), (3,8), (4,5), (5,6).

**Ví dụ ô tô** (tr. 93): trục X = tuổi xe, trục Y = vận tốc khi đi qua. Câu hỏi: "Xe càng mới chạy càng nhanh?" → các điểm dốc xuống gợi ý **tương quan âm**.

### Nhiều scatter trên một hệ trục và tô màu

tr. 94 · tr. 95 · tr. 96

```python
# ngày 1: tuổi và tốc độ 13 xe
x = np.array([5, 7, 8, 7, 2, 17, 2, 9, 4, 11, 12, 9, 6])
y = np.array([99, 86, 87, 88, 111, 86, 103, 87, 94, 78, 77, 85, 86])
plt.scatter(x, y)                       # mặc định xanh lam
# ngày 2: 15 xe
x = np.array([2, 2, 8, 1, 15, 8, 12, 9, 7, 3, 11, 4, 7, 14, 12])
y = np.array([100, 105, 84, 105, 90, 99, 90, 95, 94, 100, 79, 112, 91, 80, 85])
plt.scatter(x, y)                       # tự đổi sang cam
```

- Gọi **`scatter`** hai lần → **hai màu mặc định khác nhau: xanh lam rồi cam** (chu trình màu).
- Đặt màu cho cả loạt: **`plt.scatter(x, y, color='hotpink')`**, *`color='#88c999'`*.
- Mỗi điểm một màu: truyền **mảng màu** vào tham số **`c`**:

```python
colors = np.array(["red", "green", "blue", "yellow", "pink", "black", "orange",
                   "purple", "beige", "brown", "gray", "cyan", "magenta"])
plt.scatter(x, y, c=colors)     # 13 điểm, 13 màu; len(colors) phải = len(x)
```

> **warning** Dễ nhầm
> `color=` đặt **một** màu cho cả loạt. `c=` nhận **một màu cho mỗi điểm** (mảng). Độ dài mảng *`c`* phải khớp số điểm.

## Hàm stackplot()

tr. 97 · tr. 98

**Biểu đồ ngăn xếp** (diện tích xếp chồng): vẽ các tập dữ liệu **chồng lên nhau theo chiều dọc**.

```python
matplotlib.pyplot.stackplot(x, *args, labels=(), colors=None, baseline='zero', data=None, **kwargs)
```

```python
x = [1, 2, 3, 4, 5]
y1 = [1, 1, 2, 3, 5]    # Fibonacci
y2 = [0, 4, 2, 6, 8]    # Evens
y3 = [1, 3, 5, 7, 9]    # Odds
y = np.vstack([y1, y2, y3])
labels = ["Fibonacci ", "Evens", "Odds"]
fig, ax = plt.subplots()
ax.stackplot(x, y1, y2, y3, labels=labels)
ax.legend(loc='upper left')
```

Mép trên cùng tại mỗi x = tổng ba lớp: **`y.sum(axis=0)`** → `[2, 8, 9, 16, 22]` (đã chạy). Lớp dưới cùng là y1 (xanh), rồi y2 (cam), rồi y3 (xanh lá).

> **tip** Mẹo thi
> Muốn đọc **riêng** lớp giữa tại x = 4: lấy mép trên trừ mép dưới = $(3+6) - 3 = 6$ = y2[3]. Stackplot là **area chart xếp lớp** thuộc nhóm thành phần ([7.2.3](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md)).

> **question** Tự kiểm tra
> 1. **`plt.plot(x, y, 'k:')`** vẽ gì?
> > Đường chấm chấm màu đen, không marker.
> 2. **`plt.plot(x, y, 'g^')`** có đường nối không?
> > Không, chỉ marker tam giác xanh lá.
> 3. Viết tắt của `markerfacecolor`, *`linestyle`*, *`linewidth`*?
> > `mfc`, `ls`, *`lw`*.
> 4. **`plt.hist([1,1,2,2,2,3], bins=2)`** cho `n` bằng bao nhiêu?
> > Biên 1, 2, 3. Khoảng [1,2) có 1,1 → 2; khoảng [2,3] có 2,2,2,3 → 4. `n = [2, 4]`.
> 5. Ở **`barh`**, tham số nào là độ dài thanh?
> > *`width`*.
> 6. *`autopct='%1.1f%%'`* làm gì?
> > Ghi phần trăm 1 chữ số thập phân trên mỗi lát.

**Áp dụng ở.** F703 Màu, kiểu đường, marker và chú giải · F709 Đọc phân phối – histogram, boxplot, violin, KDE · F711 Đọc biểu đồ cột, đường và tỷ lệ · Tiếp theo: [08 Chương 07 - Trục chú giải lưu hình và cấu hình](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md).
