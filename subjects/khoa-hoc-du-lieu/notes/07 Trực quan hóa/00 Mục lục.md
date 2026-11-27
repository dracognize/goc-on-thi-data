# Chương 07 · Trực quan hóa

> **abstract** Đầu ra
> Từ một câu hỏi phân tích: chọn đúng loại biểu đồ, đọc được boxplot/histogram/scatter, nhận ra bẫy thiết kế, và viết hoặc đọc code matplotlib · pandas · seaborn tương ứng (tham số, giá trị trả về, kết quả).

**Cần biết trước.** Chọn cột Pandas, bảng dài/rộng, khóa nhóm, tổng hợp — xem [hàng, cột và index](../03%20NumPy%20v%C3%A0%20Pandas/04%20Index%20v%C3%A0%20c%C4%83n%20ch%E1%BB%89nh%20Pandas.md).

**Áp dụng ở.** [05 Chương 08 - Ma trận nhầm lẫn và chỉ số](../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md) khi trực quan hóa kết quả đánh giá.

## Thứ tự đọc

1. [06 Chương 07 - Tổng quan và nguyên tắc thiết kế](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md) · 7.1 vai trò, nguyên tắc, lỗi thiết kế.
2. [01 Chương 07 - Chọn và đọc biểu đồ](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) · 7.2 phân phối, so sánh, thành phần, quan hệ, small multiples.
3. [03 Chương 07 - Figure Axes và dữ liệu vẽ](03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md) · 7.3.1–7.3.2 Figure, add_subplot, subplots.
4. [07 Chương 07 - Các hàm vẽ Matplotlib](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) · 7.3.3 plot, fmt, bar, barh, pie, hist, scatter, stackplot.
5. [08 Chương 07 - Trục chú giải lưu hình và cấu hình](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) · 7.3.4–7.3.6 trục, legend, annotate, patch, savefig, rc.
6. [09 Chương 07 - Pandas và Seaborn](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) · 7.4 pandas plot, barplot, histplot, regplot, pairplot, catplot.
7. [04 Chương 07 - Công thức và cú pháp](04%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md) · bảng tra nhanh.
8. [05 Chương 07 - Tự kiểm tra](05%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%B1%20ki%E1%BB%83m%20tra.md) → Thẻ nhớ chương 7 (tag `#flashcards/chuong-7`).
9. Đọc thêm: [Thực hành thêm - Bố cục chú thích và biểu đồ tỷ lệ](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20B%E1%BB%91%20c%E1%BB%A5c%20ch%C3%BA%20th%C3%ADch%20v%C3%A0%20bi%E1%BB%83u%20%C4%91%E1%BB%93%20t%E1%BB%B7%20l%E1%BB%87.md).

## Bản đồ chương



## Sơ đồ Excalidraw

| Sơ đồ | Trả lời câu hỏi |
| --- | --- |
| [02 Chọn biểu đồ.excalidraw](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/02%20Ch%E1%BB%8Dn%20bi%E1%BB%83u%20%C4%91%E1%BB%93.excalidraw.md) | Câu hỏi phân tích nào → biểu đồ nào? |
| [Giải phẫu boxplot.excalidraw](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/Gi%E1%BA%A3i%20ph%E1%BA%ABu%20boxplot.excalidraw.md) | Râu dừng ở đâu, điểm nào là ngoại lai? |
| [Lưới subplot và chỉ số.excalidraw](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/L%C6%B0%E1%BB%9Bi%20subplot%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.excalidraw.md) | **`add_subplot(r,c,k)`** ứng với `axes[i,j]` nào? |
| [Giải mã format string.excalidraw](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/Gi%E1%BA%A3i%20m%C3%A3%20format%20string.excalidraw.md) | `'ro--'`, `'bs'`, `'k:'` nghĩa là gì? |
| [Annotate xy và xytext.excalidraw](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/Annotate%20xy%20v%C3%A0%20xytext.excalidraw.md) | Trong **`annotate`**, chữ ở đâu, mũi tên chỉ đâu? |
| [hue col row trong catplot.excalidraw](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/hue%20col%20row%20trong%20catplot.excalidraw.md) | *`hue`*, *`col`*, *`row`* chia lưới thế nào? |

## Phủ slide (Lec7, 164 trang)

| Trang | Chủ đề | Note |
| --- | --- | --- |
| 1–2 | Bìa, mục lục bài giảng | Không có nội dung thi |
| 3–8 | 7.1.1 Giới thiệu, matplotlib, `%matplotlib inline` | [7.1.1](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md) |
| 9–11 | 7.1.2 Vai trò: khám phá, giải thích, biểu đồ vs bảng | [7.1.2](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md) |
| 12–15 | 7.1.3 Rõ ràng, trung thực, có mục tiêu; kể chuyện | [7.1.3](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md) |
| 16–21 | 7.1.4 Trục từ 0, 3D, màu, nhãn | [7.1.4](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md) |
| 22–24 | 7.2 Nhóm biểu đồ theo mục đích | [7.2 tóm tắt](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| 25–33 | 7.2.1 Histogram, density, boxplot, violin | [7.2.1](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| 34–39 | 7.2.2 Bar, line, dot plot | [7.2.2](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| 40–45 | 7.2.3 Pie, donut, stacked, area | [7.2.3](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| 46–52 | 7.2.4 Scatter, bubble, line, heatmap | [7.2.4](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| 53–57 | 7.2.5 Small multiples | [7.2.5](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| 58–61 | 7.3.1 Import, **`plt.plot(data)`** | [7.3.1](03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md) |
| 62–73 | 7.3.2 Figure, add_subplot, subplots, subplots_adjust | [7.3.2](03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md) |
| 74–81 | 7.3.3 **`plot()`**, kiểu đường, format string | [plot](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) |
| 82–86 | **`bar()`**, **`barh()`** | [bar](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) · [barh](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) |
| 87 | **`pie()`** | [pie](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) |
| 88–90 | **`hist()`**, ví dụ 250 người | [hist](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) |
| 91–96 | **`scatter()`**, *`color`*, *`c`* | [scatter](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) |
| 97–98 | **`stackplot()`** | [stackplot](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) |
| 99–109 | 7.3.4 xlim, ticks, labels, title, **`ax.set`** | [7.3.4](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) |
| 110–117 | 7.3.5 legend, text, annotate, patches | [7.3.5](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) |
| 118–119 | 7.3.6 savefig | [savefig](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) |
| 120–130 | 7.3.6 rc, rcParams, style, matplotlibrc | [cấu hình](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) |
| 131–133 | 7.4 Giới thiệu seaborn | [7.4 tóm tắt](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| 134–139 | 7.4.1 Series/DataFrame plot | [7.4.1](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| 140–149 | 7.4.2 plot.bar, crosstab, sns.barplot | [7.4.2](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| 150–153 | 7.4.3 plot.hist, density, histplot | [7.4.3](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| 154–158 | 7.4.4 regplot, pairplot | [7.4.4](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| 159–163 | 7.4.5 catplot, facet | [7.4.5](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| 164 | Trang kết | Không có nội dung thi |

Các trang 4, 9, 12, 16, 23, 25, 34, 40, 46, 53, 59, 62, 74, 99, 111, 133, 140, 150, 154, 159 là trang chuyển mục (chỉ lặp mục lục).

## Họ bài tập chương 7

Mở chỉ mục các họ bài của chương 7.

| Họ | Học trước ở |
| --- | --- |
| F701 Chọn loại biểu đồ theo câu hỏi | [01 Chương 07 - Chọn và đọc biểu đồ](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| F702 Figure, Axes và bố cục subplot | [03 Chương 07 - Figure Axes và dữ liệu vẽ](03%20Ch%C6%B0%C6%A1ng%2007%20-%20Figure%20Axes%20v%C3%A0%20d%E1%BB%AF%20li%E1%BB%87u%20v%E1%BA%BD.md) |
| F703 Màu, kiểu đường, marker và chú giải | [07 Chương 07 - Các hàm vẽ Matplotlib](07%20Ch%C6%B0%C6%A1ng%2007%20-%20C%C3%A1c%20h%C3%A0m%20v%E1%BA%BD%20Matplotlib.md) |
| F704 Giới hạn trục, vạch chia và thang log | [08 Chương 07 - Trục chú giải lưu hình và cấu hình](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) |
| F705 Chú thích, chữ và hình trên biểu đồ | [08 Chương 07 - Trục chú giải lưu hình và cấu hình](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) |
| F706 Lưu hình, dpi và cấu hình toàn cục | [08 Chương 07 - Trục chú giải lưu hình và cấu hình](08%20Ch%C6%B0%C6%A1ng%2007%20-%20Tr%E1%BB%A5c%20ch%C3%BA%20gi%E1%BA%A3i%20l%C6%B0u%20h%C3%ACnh%20v%C3%A0%20c%E1%BA%A5u%20h%C3%ACnh.md) |
| F707 Vẽ bằng Pandas – Series.plot và DataFrame.plot | [09 Chương 07 - Pandas và Seaborn](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| F708 Seaborn – thống kê vẽ sẵn và giao diện | [09 Chương 07 - Pandas và Seaborn](09%20Ch%C6%B0%C6%A1ng%2007%20-%20Pandas%20v%C3%A0%20Seaborn.md) |
| F709 Đọc phân phối – histogram, boxplot, violin, KDE | [01 Chương 07 - Chọn và đọc biểu đồ](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| F710 Đọc quan hệ hai biến và tương quan | [01 Chương 07 - Chọn và đọc biểu đồ](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| F711 Đọc biểu đồ cột, đường và tỷ lệ | [01 Chương 07 - Chọn và đọc biểu đồ](01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md) |
| F712 Công cụ dashboard và trực quan tương tác | [06 Chương 07 - Tổng quan và nguyên tắc thiết kế](06%20Ch%C6%B0%C6%A1ng%2007%20-%20T%E1%BB%95ng%20quan%20v%C3%A0%20nguy%C3%AAn%20t%E1%BA%AFc%20thi%E1%BA%BFt%20k%E1%BA%BF.md) |

## Phân tích chuyên sâu

So sánh phân phối hai nhóm kích thước 100 và 1.000 trong khi cần thấy cả ngoại lệ và dạng phân phối.

> **check** Lập luận và ca biên
> Dùng histogram với cùng biên bin và mật độ hoặc tỷ lệ để so dạng. Dùng boxplot bổ sung để nhìn trung vị, IQR và các điểm ngoài hàng rào. Gắn đơn vị, cỡ mẫu và quy tắc bin. Ngoại lệ trên hình cần xác minh.
