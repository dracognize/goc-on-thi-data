# Công thức và cú pháp · Chương 6

Trước khi chọn hàm, phân biệt **bổ sung thông tin theo khóa**, **xếp cạnh theo nhãn** và **đổi bố cục trên cùng dữ liệu**. Tra ví dụ trong [MultiIndex](01%20MultiIndex.md), [ghép bảng](03%20Merge%20concat%20v%C3%A0%20combine_first.md) và [đổi dạng](04%20Melt%20pivot%20stack%20v%C3%A0%20unstack.md).

| Tác vụ | Công thức hoặc cú pháp | Kiểm tra |
| --- | --- | --- |
| Đếm inner join | $\sum_k n_L(k)n_R(k)$ | Mỗi khóa chung tạo mọi cặp khớp |
| Tạo index nhiều cấp | **`df.set_index(["vung", "thang"])`** | Thứ tự tên cột quyết định thứ tự cấp |
| Chọn một giá trị của cấp | **`df.xs("HN", level="vung")`** | Cấp lọc mặc định biến mất khỏi kết quả |
| Kiểm tra quan hệ nhiều–một | **`L.merge(R, on='id', how='left', validate='many_to_one')`** | Khóa bảng phải phải duy nhất |
| Xếp theo hàng | **`pd.concat([a, b], axis=0, ignore_index=True)`** | Căn cột theo nhãn |
| Xếp theo cột | **`pd.concat([a, b], axis=1)`** | Căn hàng theo nhãn index |
| Điền từ bảng phụ | **`a.combine_first(b)`** | Bên trái ưu tiên nếu ô đã có giá trị |
| Wide sang long | **`df.melt(id_vars=['id'], value_vars=['Q1','Q2'])`** | Giữ khóa hàng và ghi biến đo |
| Long sang wide | **`df.pivot_table(index='id', columns='q', values='v', aggfunc='sum')`** | Kiểm tra phép tổng hợp có đúng ngữ nghĩa |
| Di chuyển cấp | **`df.stack(level=-1)`**, **`df.unstack(level=-1)`** | Theo dõi cấp đi từ cột xuống hàng hoặc từ hàng lên cột |
| Đổi thứ tự cấp | **`df.swaplevel(0, 1).sort_index()`** | swaplevel không tự sắp dòng (tr. 25) |
| Chọn cấp trong bằng loc | `df.loc[(slice(None), 'Online'), :]` | **`slice(None)`** = lấy mọi nhãn cấp ngoài (tr. 43) |
| Thống kê theo cấp | **`df.groupby(level=0).describe()`** | 8 thống kê mỗi nhóm (tr. 34) |
| Merge cột trái – index phải | **`pd.merge(L, R, left_on='k', right_index=True)`** | Index kết quả lấy từ bảng trái (tr. 61) |
| Đếm cross join | $N_L \times N_R$ | Không dùng khóa (tr. 52) |
| Gắn nguồn khi concat | **`pd.concat([a, b], keys=['A', 'B'])`** | Thêm cấp nhãn ngoài (tr. 69) |
| Long sang wide không tổng hợp | **`df.pivot(index=..., columns=..., values=...)`** | Cặp (index, columns) phải duy nhất (tr. 94) |
| Ô thiếu khi unstack | **`s.unstack(fill_value=0)`** | Thay NaN bằng 0 (tr. 102) |

Ôn bằng Thẻ nhớ chương 6 · Sơ đồ chọn hàm.

Mục lục chương 6
