# Công thức và cú pháp · Chương 07

> **abstract** Tóm tắt
> Trang tra nhanh toàn chương. Mỗi dòng có link về note giải thích chi tiết.

## Công thức

| Đại lượng | Công thức | Ghi chú |
| --- | --- | --- |
| Khoảng tứ phân vị | $IQR = Q_3 - Q_1$ | 50% dữ liệu giữa ([boxplot](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md)) |
| Hàng rào ngoại lai | $[\,Q_1 - 1.5IQR,\; Q_3 + 1.5IQR\,]$ | Ngoài đoạn → ngoại lai. Râu dừng ở **quan sát thật** gần hàng rào nhất |
| Độ rộng bin khi *`bins=k`* | $\dfrac{\max - \min}{k}$ | Bin cuối gồm cả max |
| Kích thước ảnh (pixel) | $\text{figsize} \times \text{dpi}$ | Mặc định $6.4 \times 4.8$ inch × 100 = 640×480 |
| Tỷ lệ tiền boa (slide) | $\text{tip\_pct} = \dfrac{\text{tip}}{\text{total\_bill} - \text{tip}}$ | Ví dụ tips |
| Chuẩn hóa theo hàng | **`df.div(df.sum(axis="columns"), axis="index")`** | Mỗi hàng tổng = 1 |
| Ô subplot | **`add_subplot(r, c, k)`** ↔ `axes[(k-1)//c, (k-1)%c]` | k từ 1, chỉ số từ 0 |

Ví dụ: $Q_1 = 10$, $Q_3 = 22$ → $IQR = 12$, hàng rào $[-8, 40]$. Nếu 38 là giá trị lớn nhất ≤ 40, râu trên dừng ở 38.

## Matplotlib · tạo hình

| Nhu cầu | Cú pháp | Note |
| --- | --- | --- |
| Hiện hình trong notebook | `%matplotlib inline` | [7.1.1](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md) |
| Tạo Figure | **`plt.figure(num, figsize, dpi, facecolor, edgecolor, tight_layout)`** | [Figure](03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md) |
| Thêm một ô | **`fig.add_subplot(nrows, ncols, index)`** | [add_subplot](03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md) |
| Figure + lưới ô | `fig, axes = plt.subplots(nrows, ncols, sharex, sharey, squeeze, figsize, layout)` | [subplots](03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md) |
| Khoảng cách ô | **`plt.subplots_adjust(left, right, bottom, top, wspace, hspace)`** | wspace ngang, hspace dọc |

## Matplotlib · hàm vẽ



> **note** Bảng dạng chữ
> | Hàm | Cú pháp | Ghi nhớ |
> | --- | --- | --- |
> | Đường | **`plt.plot([x], y, [fmt], data=None, **kw)`** | Trả **list Line2D**. Một mảng → là y |
> | Format | `'ro--'` = `[color][marker][line]` | `k` = black, *`b`* = blue |
> | Kiểu đường | `color/c`, `linestyle/ls`, `linewidth/lw`, *`marker`*, `markersize/ms`, `markerfacecolor/mfc`, `markeredgecolor/mec` | |
> | Cột | **`plt.bar(x, height, width=0.8, bottom=None, align='center')`** | |
> | Thanh ngang | **`plt.barh(y, width, height=0.8, left=None)`** | *`width`* = độ dài |
> | Tròn | **`plt.pie(values, labels=..., autopct='%1.1f%%')`**, **`plt.axis('equal')`** | ≤ 6 nhóm |
> | Histogram | `n, bins, patches = plt.hist(data, bins=5)` | `len(bins) = k + 1` |
> | Scatter | **`plt.scatter(x, y, s, c, marker, cmap, alpha, ...)`** | *`c`* = mảng màu từng điểm |
> | Diện tích chồng | **`ax.stackplot(x, y1, y2, y3, labels=..., baseline='zero')`** | Mép trên = tổng |

Chi tiết: [07 Chương 07 - Các hàm vẽ Matplotlib](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md).

## Matplotlib · trục, chú giải, lưu, cấu hình

| Nhu cầu | Cú pháp |
| --- | --- |
| Đọc / đặt giới hạn | **`ax.get_xlim()`** / **`ax.set_xlim([0, 10])`** (**`plt.xlim()`** tương ứng) |
| Vạch chia | **`ax.set_xticks(ticks, minor=False)`**, **`ax.set_xticklabels(labels, rotation=30, fontsize=8)`** |
| Nhãn, tiêu đề | **`ax.set_xlabel(s, labelpad=10, loc='center')`**, **`ax.set_title(s, pad=12, loc='center')`** |
| Nhiều thuộc tính | **`ax.set(title=, xlabel=, ylabel=, xlim=, ylim=, xticks=, yticks=)`** |
| Chú giải | `label=` khi vẽ + **`ax.legend(loc, title, fontsize, frameon, shadow, bbox_to_anchor)`** |
| Mã *`loc`* | 0 best · 1 upper right · 2 upper left · 3 lower left · 4 lower right · 5 right · 6 center left · 7 center right · 8 lower center · 9 upper center · 10 center |
| Chữ | **`ax.text(x, y, s, fontdict=..., ha=, va=, rotation=, bbox=)`** |
| Mũi tên | **`ax.annotate(s, xy=điểm, xytext=chữ, arrowprops=dict(arrowstyle="->"))`** |
| Hình | **`ax.add_patch(plt.Rectangle((x,y), w, h))`**, **`plt.Circle((x,y), r)`**, **`plt.Polygon([...])`** |
| Lưu | **`fig.savefig(fname, dpi=300, bbox_inches="tight", transparent=True, format=None)`** |
| Cấu hình nhóm | **`plt.rc('font', size=12)`** |
| Cấu hình khóa | `mpl.rcParams['figure.figsize'] = [8, 5]`, **`mpl.rcParams.update({...})`** |
| Style | **`plt.style.use('ggplot')`**, `'grayscale'` |
| Tạm thời | `with plt.rc_context({...}):` |
| Về mặc định | **`mpl.rcdefaults()`** |

Chi tiết: [08 Chương 07 - Trục chú giải lưu hình và cấu hình](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md).

## Pandas và Seaborn

| Nhu cầu | Cú pháp | Ghi nhớ |
| --- | --- | --- |
| Đường | **`s.plot()`**, **`df.plot()`** ≡ **`df.plot.line()`** | *`kind`* mặc định `"line"`, index → trục x |
| Tham số plot | `label, ax, style, alpha, kind, figsize, logx, logy, title, use_index, rot, xticks, yticks, xlim, ylim, grid` | |
| Mỗi cột một ô | **`df.plot(subplots=True, layout=(2, 2), sharex=True)`** | |
| Cột | **`s.plot.bar()`**, **`df.plot.barh(stacked=True)`** | Không tổng hợp |
| Tần suất giá trị | **`s.value_counts().plot.bar()`** | |
| Bảng chéo | **`pd.crosstab(df["a"], df["b"])`** | |
| Histogram / mật độ | **`s.plot.hist(bins=50)`**, **`s.plot.density()`** (= *`kind="kde"`*) | |
| Seaborn cột | **`sns.barplot(x=, y=, hue=, data=, orient="h")`** | **Trung bình** + khoảng tin cậy |
| Đếm | **`sns.countplot(data=df, x="nhom")`** | Số dòng |
| Seaborn histogram | **`sns.histplot(values, bins=100, kde=True)`** | |
| Scatter + hồi quy | **`sns.regplot(x=, y=, data=)`** | Trả Axes |
| Ma trận scatter | **`sns.pairplot(df, diag_kind="kde", plot_kws={"alpha": 0.8})`** | Trả PairGrid |
| Lưới đa diện | **`sns.catplot(x=, y=, hue=, col=, row=, kind="bar"/"box", data=)`** | Trả FacetGrid |

Chi tiết: [09 Chương 07 - Pandas và Seaborn](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md).

## Bảng đầu vào nhỏ → kết quả (đã chạy)



> **note** Bảng dạng chữ
> | Lệnh | Đầu vào | Kết quả |
> | --- | --- | --- |
> | **`plt.hist(d, bins=5)`** | `[1,2,2,3,3,3,4,4,5]` | `n = [1, 2, 3, 2, 1]` |
> | **`ax.hist(x, bins=[0,15,30])`** | `[9, 12, 19, 20]` | `n = [2, 2]` |
> | **`plt.plot([1,2],[3,4],'ro--')`** | — | 1 Line2D, màu `r`, marker `o`, kiểu `--` |
> | **`plt.subplots(2, 3)`** | — | `axes.shape = (2, 3)` |
> | **`plt.subplots(1, 2)`** | — | `axes.shape = (2,)` |
> | **`plt.figure()`** | — | `<Figure size 640x480 with 0 Axes>` |
> | **`type(plt.Rectangle(...))`** | — | `matplotlib.patches.Rectangle` |
> | **`np.percentile(d,[25,50,75])`** | `[2,4,4,5,6,7,8,9,30]` | `4, 6, 8` → IQR 4, hàng rào [−2, 14] |

**Đọc tứ phân vị.** Với ít quan sát, các quy ước nội suy có thể cho $Q_1, Q_3$ hơi khác nhau. Đề cho sẵn $Q_1, Q_3$ thì dùng trực tiếp.

Nguồn tr. 30 · tr. 75 · tr. 100 · tr. 118 · tr. 128 · tr. 135
