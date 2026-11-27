# Thực hành thêm · Bố cục, chú thích và biểu đồ tỷ lệ

## Bố cục, chú thích, patch và xuất hình

**Figure** là toàn bộ hình. **Axes** là một vùng vẽ, có dữ liệu, thang đo, tiêu đề và nhãn trục riêng. **Patch** là hình học được vẽ thêm vào một Axes. Ví dụ dùng **`Rectangle`** để làm rõ khoảng thời gian, và dùng mũi tên để chỉ giá trị cao nhất. Lec 7 · Figure và Axes · Khoảng giữa subplots

```python
import matplotlib as mpl
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle

months = [1, 2, 3]
sales = [10, 16, 12]
with mpl.rc_context({"font.size": 10, "axes.grid": True}):
    fig, (left, right) = plt.subplots(1, 2, figsize=(9, 3.4))
    fig.subplots_adjust(wspace=0.42, bottom=0.2)
    left.plot(months, sales, marker="o", label="Doanh số")
    left.set(xlabel="Tháng", ylabel="Triệu đồng", title="Diễn biến")
    left.add_patch(Rectangle((1.75, 0), 0.5, 20, alpha=0.15, color="gold"))
    left.text(1.0, 8.7, "Quý I")
    left.annotate("Đỉnh: 16", xy=(2, 16), xytext=(2.18, 17.5),
                  arrowprops={"arrowstyle": "->"})
    left.set_ylim(8, 19)
    left.legend()

    right.bar(months, sales, color="#31778f")
    right.set(xlabel="Tháng", ylabel="Triệu đồng", title="So sánh")
    right.set_xticks(months)
    fig.savefig("doanh-so-quy-1.png", dpi=160, bbox_inches="tight")
    plt.show()
```

- **`subplots_adjust`** chỉnh bố cục. *`wspace`* tăng khoảng ngang giữa hai Axes. *`bottom`* tăng chỗ cho nhãn bên dưới.
- `left.text` đặt chữ tại tọa độ. `left.annotate` tách *đích mũi tên* *`xy`* khỏi *vị trí chữ* *`xytext`*. **`Rectangle`** nhận góc dưới trái, chiều rộng và chiều cao trong hệ tọa độ dữ liệu.
- Legend lấy nhãn từ `label=`. **`fig.savefig`** lưu đúng Figure đang giữ trong biến. *`dpi`* ảnh hưởng độ phân giải ảnh raster. *`bbox_inches="tight"`* giúp lấy cả các nhãn gần mép.
- **`mpl.rc("font", size=10)`** đặt mặc định theo nhóm. `mpl.rcParams["font.size"]` truy cập theo khóa. `mpl.rc_context` áp dụng tạm thời để ví dụ không đổi kiểu các hình tiếp theo.
- Trục trái được thu hẹp để thấy thay đổi của đường. Trục cột bên phải giữ mốc 0 để chiều dài cột biểu diễn độ lớn đúng.

Lec 7 · Legend đến patch · Lưu hình · Style và rcParams

## Từ bảng đếm tới tỷ lệ theo hàng

Dùng dữ liệu nhỏ thay cho `tips.csv`. Nhập món và kích cỡ nhóm, rồi thử dự đoán số quan sát theo từng cặp trước khi chạy.

```python
import pandas as pd

tips = pd.DataFrame({
    "ngay": ["Thứ Sáu", "Thứ Sáu", "Thứ Sáu", "Thứ Bảy", "Thứ Bảy"],
    "so_khach": [2, 2, 4, 2, 4],
    "ca": ["Ngày", "Tối", "Tối", "Ngày", "Tối"],
    "boa": [2, 4, 5, 3, 6],
    "hoa_don": [18, 20, 30, 16, 24],
})
tips["ty_le_boa"] = tips["boa"].div(tips["hoa_don"])
counts = pd.crosstab(tips["ngay"], tips["so_khach"])
row_total = counts.sum(axis="columns")
proportions = counts.div(row_total, axis="index")
assert counts.loc["Thứ Sáu"].tolist() == [2, 1]
assert counts.loc["Thứ Bảy"].tolist() == [1, 1]
assert proportions.sum(axis=1).round(8).eq(1).all()
```

[![C7 Thực hành thêm - Bố cục chú thích và biể – bảng 1](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C7%20Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20B%E1%BB%91%20c%E1%BB%A5c%20ch%C3%BA%20th%C3%ADch%20v%C3%A0%20bi%E1%BB%83%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.svg)](../../diagrams/07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/B%E1%BA%A3ng%20tr%E1%BB%B1c%20quan/C7%20Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20B%E1%BB%91%20c%E1%BB%A5c%20ch%C3%BA%20th%C3%ADch%20v%C3%A0%20bi%E1%BB%83%20%E2%80%93%20b%E1%BA%A3ng%201.excalidraw.md)

> **note** Bảng dạng chữ
> | Nhóm | Số bàn 2 khách | Số bàn 4 khách | Tỷ lệ 2 khách | Tỷ lệ 4 khách |
> | --- | ---: | ---: | ---: | ---: |
> | Thứ Sáu | 2 | 1 | 2/3 | 1/3 |
> | Thứ Bảy | 1 | 1 | 1/2 | 1/2 |

**`sum(axis="columns")`** cộng qua các cột để lấy tổng **mỗi hàng**. **`div(..., axis="index")`** dùng tên ngày căn đúng mẫu số. Muốn đọc thành phần, dùng **`proportions.plot.bar(stacked=True)`** với thang dọc từ 0 đến 1. Nhớ nêu cả cỡ mẫu vì hai ngày có số bàn khác nhau. Lec 7 · crosstab, tổng theo hàng và tỷ lệ

## Khi nào dùng facet?

Facet tách từng nhóm con thành một ô vẽ trên cùng thang so sánh. Chạy khối này sau khi tạo bảng `tips` phía trên. *`col="ca"`* tạo một ô cho ca ngày và một ô cho ca tối. *`kind="strip"`* giữ từng quan sát để người học đọc được cỡ mẫu nhỏ.

```python
import matplotlib.pyplot as plt
import seaborn as sns

chart = sns.catplot(data=tips, x="ngay", y="ty_le_boa", col="ca",
                    kind="strip", sharey=True)
chart.set_axis_labels("Ngày", "Tỷ lệ tiền boa")
plt.show()
```

Màu qua *`hue`* chia nhóm trong cùng ô. *`col`* hoặc *`row`* chia thành các ô. Khi dùng *`kind="bar"`*, đọc phép tổng hợp và chú thích bất định. Khi dùng *`kind="box"`*, đọc phân phối thay cho một giá trị tóm tắt. Lec 7 · catplot và nhóm phân loại · [Về mục lục Lec 7](00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
