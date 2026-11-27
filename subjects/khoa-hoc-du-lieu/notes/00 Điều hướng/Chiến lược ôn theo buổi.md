# Chiến lược ôn theo buổi

Bắt đầu từ **Ngày 1** bất cứ khi nào sẵn sàng. Lộ trình chuẩn có **9 ngày học, 16 buổi**, mỗi buổi 75 phút. Nếu chỉ học được một buổi mỗi ngày, tách ngày có hai buổi thành hai ngày và giữ thứ tự các buổi. Khi học hai buổi, nghỉ ít nhất 20 phút giữa hai buổi.

Mỗi buổi tạo ra một kết quả tự kiểm tra được. Với bài đọc code, chốt đầu ra trước khi chạy. Với bài xử lý bảng, dự đoán kiểu dữ liệu, số hàng hoặc shape trước khi gọi hàm. Với câu trắc nghiệm, ghi lý do chọn đáp án rồi mới chấm.

## Chọn nhịp học

| Thời gian có thể dành | Cách đi qua lộ trình |
| --- | --- |
| 16 buổi | Theo thứ tự đầy đủ. Dùng kết quả Đề A để chọn trọng tâm sửa lỗi trước Đề B. |
| 10–15 buổi | Dành 1 buổi chẩn đoán, 3–8 buổi cho chương yếu, 2 buổi thực hành liên chương, 2 buổi làm đề, 1 buổi sửa lỗi và 1 buổi kiểm tra lại. Giữ thứ tự học kiến thức nền trước bài tổng hợp. |
| 5–9 buổi | Dành 1 buổi chẩn đoán, 2–6 buổi cho các họ sai hoặc đoán lặp lại, 1 buổi làm đề đủ 40 phút và 1 buổi sửa lỗi bằng câu mới. Ưu tiên các lỗi xuất hiện ở nhiều chương, như nhầm shape, khóa nối hay fit trên tập kiểm tra. |
| 3–4 buổi | Buổi 1 làm một đề đủ 40 phút và phân loại lỗi. Buổi 2 sửa hai họ sai nhiều nhất. Các buổi còn lại làm biến thể mới, rồi luyện một lượt hỗn hợp có bấm giờ. |
| Chỉ có 30 phút hôm nay | Dùng 5 phút nhớ lại, 15 phút làm 4–6 câu mới thuộc một họ yếu và 10 phút chữa. Dời phần còn lại sang buổi kế tiếp. |

Trong **Ghi chú**, mở chương tương ứng để tra đúng phần vướng. Dùng **Câu hỏi** để lấy mẫu chẩn đoán theo chương, **Luyện theo họ** để khoanh một kỹ năng và **Đề thi** để đo tốc độ làm bài. Dùng **Flashcard** cho quy tắc, cú pháp và công thức đã học.

## Ngày 1 · Chẩn đoán, quy trình khoa học dữ liệu và Python

### Buổi 1 · Chẩn đoán và Chương 1

- **0–25 phút.** Làm 16 câu mới, mỗi chương 2 câu. Ghi bên cạnh mỗi mã câu một trong ba dấu: chắc, phân vân, đoán. Kết quả chỉ dùng để chọn điểm bắt đầu vì mẫu mỗi chương còn nhỏ.
- **25–45 phút.** Viết lại luồng từ câu hỏi nghiệp vụ đến kết quả có thể sử dụng. Lập bảng cho ba tình huống: dự đoán doanh thu, phát hiện thư rác và phân nhóm khách hàng. Ghi mục tiêu, dữ liệu đầu vào, có hay không có nhãn và đầu ra mong muốn.
- **45–65 phút.** Làm 6 câu mới về loại bài toán, vai trò dữ liệu và quy trình. Với mỗi câu sai, chỉ ra từ khóa trong đề đã bị bỏ qua.
- **65–75 phút.** Chốt hai chương cần kiểm tra thêm. Đạt buổi khi phân loại đúng ba tình huống và giải thích được vì sao phân nhóm khách hàng có thể thực hiện khi chưa có nhãn.

### Buổi 2 · Chương 2 — đọc code bằng bảng trạng thái

- **0–10 phút.** Tự viết ví dụ về danh sách có thể thay đổi, chuỗi bất biến và một hàm nhận danh sách.
- **10–30 phút.** Trace sáu đoạn ngắn về slicing, vòng lặp, hàm và alias. Với `b = a` và `b = a[:]`, vẽ hai cột giá trị của `a` và `b` sau mỗi lệnh. Thử thêm trường hợp danh sách lồng nhau.
- **30–60 phút.** Làm 10 câu mới về kiểu dữ liệu, toán tử, luồng điều khiển và tác động của method. Với vòng lặp, ghi giá trị biến sau từng lượt. Với hàm, tách giá trị trả về khỏi tác động lên đối tượng đầu vào.
- **60–75 phút.** Chạy các đoạn dự đoán sai, tìm dòng đầu tiên làm kết quả lệch và làm lại một biến thể. Mục tiêu 8/10 câu chắc đúng và giải thích được một lỗi alias.

## Ngày 2 · Làm việc với mảng, bảng và dữ liệu nhập

### Buổi 3 · Chương 3 — shape, axis và chỉ mục

- **0–10 phút.** Ôn lại một câu alias từ Buổi 2. Vẽ mảng 2×3, tự đánh số vị trí từng phần tử.
- **10–35 phút.** Tính tay `sum(axis=0)` và `sum(axis=1)`. So sánh cộng một vector dài 3 với cộng một vector dài 2. Viết shape kết quả hoặc giải thích vì sao phép cộng không hợp lệ. Với DataFrame có nhãn dòng 10, 20, 30, thử `loc` theo nhãn và `iloc` theo vị trí.
- **35–65 phút.** Làm 10 câu về shape, broadcasting, phép giảm và chọn dòng. Với mỗi câu, ghi cả giá trị lẫn shape khi đáp án phụ thuộc vào hai yếu tố đó. Thử thêm phép cộng hai Series có tập nhãn khác nhau để thấy cách Pandas căn chỉnh nhãn.
- **65–75 phút.** Chốt một quy tắc cho trục và một quy tắc cho nhãn. Đạt buổi khi được 8/10 câu chắc đúng và tự giải được một ca nhãn số trùng với cách đánh số vị trí.

### Buổi 4 · Chương 4 — đọc tệp và kiểm tra schema

- **0–10 phút.** Viết danh sách cột mong đợi và kiểu của từng cột cho bảng đơn hàng. Chọn kiểu chuỗi cho mã nếu có thể có số 0 ở đầu.
- **10–35 phút.** Tạo một CSV có mã `001`, một ô trống, một cột ngày và một tệp JSON chứa cùng dữ liệu. Đọc cả hai, kiểm tra tên cột, số dòng, kiểu dữ liệu và số giá trị thiếu. Thử khai báo kiểu cho cột mã và chuyển cột ngày có giá trị lỗi.
- **35–60 phút.** Làm 8 câu về đọc CSV/JSON, tham số đọc, xử lý trường thiếu và chọn định dạng lưu. Với mỗi phương án, ghi một bước kiểm tra dữ liệu có thể phát hiện lỗi.
- **60–75 phút.** Viết quy trình 5 bước từ đọc đến lưu. Đạt buổi khi giải thích được vì sao một bảng đọc thành công vẫn có thể mất số 0 ở đầu hoặc có cột số bị đọc thành chuỗi.

## Ngày 3 · Làm sạch, ghép và đổi dạng dữ liệu

### Buổi 5 · Chương 5 — quyết định cách xử lý dữ liệu bẩn

- **0–10 phút.** Ôn một câu schema và một câu chỉ mục. Liệt kê các kiểu lỗi có thể có trong bảng vừa nhập.
- **10–35 phút.** Tạo bảng có một dòng trùng chính xác, hai dòng trùng mã nhưng khác giá trị, một ô thiếu và một điểm ngoại lệ. Thử chuẩn hóa khoảng trắng, đếm thiếu/trùng và giải thích cách xử lý từng trường hợp. So sánh trung vị với trung bình trên cột có ngoại lệ.
- **35–65 phút.** Làm 10 câu về thiếu/trùng, chuỗi, mã hóa và scaler. Tự so sánh thứ hạng với nhóm danh mục không có thứ tự. Giải thích rủi ro của mã số liên tiếp cho danh mục không thứ tự.
- **65–75 phút.** Lập bảng trước và sau cho số dòng, số khóa duy nhất và số giá trị thiếu. Mục tiêu 8/10 câu chắc đúng và giải thích được sự khác nhau giữa một bản ghi lặp và hai bản ghi hợp lệ có cùng mã.

### Buổi 6 · Chương 6 — đếm hàng trước khi ghép

- **0–10 phút.** Viết các khóa của bảng trái là `A, A, B` và bảng phải là `A, A, C`. Đếm số lần xuất hiện của từng khóa.
- **10–30 phút.** Dự đoán số dòng của inner, left và outer join bằng cách liệt kê cặp khớp lẫn hàng giữ lại. Đối chiếu kết quả bằng Pandas. Giải thích khi nào cần `merge` theo khóa và khi nào cần `concat` theo trục.
- **30–60 phút.** Làm 10 câu về khóa trùng, căn chỉnh nhãn và dạng wide/long. Với bảng có cột tháng, tự viết cách dùng `melt`, ghi số cột và số dòng trước khi chạy. Thử một cặp khóa lặp để xác định lúc cần tổng hợp trước khi pivot hoặc dùng `pivot_table`.
- **60–75 phút.** Làm lại một biến thể có khóa không ghép được. Đạt buổi khi dự đoán đúng số dòng của cả ba phép nối và kiểm tra được khóa nào làm dữ liệu phình lên.

## Ngày 4 · Trực quan hóa và nền tảng học có giám sát

### Buổi 7 · Chương 7 — từ câu hỏi đến biểu đồ

- **0–10 phút.** Viết ba câu hỏi liên quan đến một bảng bán hàng: so sánh nhóm, xem phân phối và xem quan hệ giữa hai biến số.
- **10–35 phút.** Chọn biểu đồ cột, histogram hoặc scatter theo từng câu hỏi. Vẽ phác trục, đơn vị, nhóm so sánh và cách xử lý dữ liệu thiếu. Với chuỗi thời gian, xem các mốc có cùng khoảng cách và dữ liệu đã được sắp xếp chưa.
- **35–60 phút.** Làm 8 câu về chọn biểu đồ, đọc trục và Figure/Axes. Tìm một biểu đồ có trục gây hiểu lầm và sửa cách trình bày. Ghi vì sao một dạng biểu đồ khác sẽ làm câu hỏi khó trả lời hơn.
- **60–75 phút.** Vẽ một biểu đồ từ bảng đã ghép và viết một kết luận có đơn vị. Đạt buổi khi người khác có thể hiểu câu hỏi và kết luận chỉ từ biểu đồ cùng chú thích.

### Buổi 8 · Chương 8 — chia dữ liệu, chọn mô hình và đo lỗi

- **0–10 phút.** Từ trí nhớ, vẽ luồng train/test và đánh dấu nơi gọi `fit`, `transform`, `predict`.
- **10–35 phút.** Tính tay khoảng cách cho KNN với 3–5 điểm, rồi xem điều gì thay đổi khi một biến có thang đo lớn. Từ một bảng dự đoán hồi quy nhỏ, tính sai số bình phương trung bình và RMSE.
- **35–65 phút.** Làm 10 câu về loại đích, KNN, hồi quy, phân loại và ma trận nhầm lẫn. Viết rõ lớp dương. Tính precision và recall, rồi giải thích chi phí của bỏ sót so với báo nhầm.
- **65–75 phút.** Sửa một ví dụ fit scaler trước khi chia tập bằng cách dựng lại đường đi đúng. Mục tiêu 8/10 câu chắc đúng và giải thích được điểm rò rỉ trong một quy trình mới.

## Ngày 5 · Thực hành liên chương

### Buổi 9 · Từ tệp thô đến bảng phân tích

- **0–10 phút.** Chọn một CSV hoặc tự tạo bảng 8–12 dòng có mã, nhóm, ngày và số lượng. Viết câu hỏi cần trả lời và đơn vị quan sát.
- **10–40 phút.** Đọc bảng, kiểm tra schema, chuẩn hóa chuỗi, xử lý thiếu và trùng, lọc một nhóm rồi tính thống kê. Sau mỗi bước ghi số dòng, kiểu cột đã đổi và một phép kiểm tra.
- **40–65 phút.** Thay dữ liệu bằng một biến thể có mã bắt đầu bằng 0, giá trị số lẫn chuỗi và một khóa trùng. Chạy lại, xác định giả định cũ nào còn đúng.
- **65–75 phút.** Viết kết luận bằng số liệu, kèm một giới hạn của dữ liệu. Đạt khi tái tạo bảng kết quả từ tệp nguồn và giải thích được mọi thay đổi số dòng.

### Buổi 10 · Từ bảng sạch đến biểu đồ có thể diễn giải

- **0–10 phút.** Chuẩn bị bảng giao dịch và bảng nhóm sản phẩm. Chọn khóa ghép, kiểu nối và số dòng dự kiến.
- **10–40 phút.** Làm sạch khóa, ghép, kiểm tra khóa không khớp, đổi wide/long nếu cần và tạo một biểu đồ so sánh. Ghi cách kiểm tra giao dịch có bị đếm hai lần hay không.
- **40–65 phút.** Thêm một khóa trùng ở bảng danh mục và một khóa mất ở bảng giao dịch. Xác định lỗi từ số dòng và tổng chỉ tiêu trước khi sửa. Chọn cách xử lý phù hợp với ý nghĩa của khóa.
- **65–75 phút.** Đạt khi dự đoán đúng thay đổi số dòng, chỉ ra một quyết định có thể làm kết luận lệch và tạo lại biểu đồ sau khi sửa.

## Ngày 6 · Luyện mô hình và lấy mốc thi thử

### Buổi 11 · Đánh giá mô hình trong tình huống mới

- **0–10 phút.** Viết tên ba bài toán có biến đích khác nhau và chỉ số tương ứng.
- **10–35 phút.** So sánh một cây sâu với một cây nông qua kết quả train/test. Với bài phát hiện lớp hiếm, tính accuracy, precision và recall từ ma trận nhầm lẫn rồi giải thích chỉ số nào phản ánh chi phí sai đã nêu.
- **35–60 phút.** Làm 8–10 câu về cây/rừng, logistic, KNN, overfitting và pipeline. Với mỗi câu sai, ghi điều kiện làm quyết định đổi, như thay lớp dương, đổi ngưỡng hoặc thay cách chia tập.
- **60–75 phút.** Tự viết một tình huống có nguy cơ rò rỉ từ dữ liệu tương lai. Giải thích cách chia dữ liệu và việc nào chỉ thực hiện trên tập train.

### Buổi 12 · Đề thử A

- **0–40 phút.** Làm Đề A một lượt liền. Gợi ý chia 25 phút lấy các câu làm chắc, 12 phút quay lại câu đánh dấu, 3 phút rà câu bỏ trống và đơn vị.
- **40–55 phút.** Chấm, ghi điểm thô và số câu chắc đúng. Đưa câu bỏ trống và đúng do đoán vào sổ lỗi.
- **55–75 phút.** Chọn tối đa ba họ ưu tiên. Với mỗi họ, ghi bước đầu tiên bị sai, quy tắc cần nhớ và một dữ kiện có thể thay để tạo câu kiểm tra. Dùng kết quả này để chọn phần sửa trước Đề B.

## Ngày 7 · Sửa lỗi và thử lại trong điều kiện thi

### Buổi 13 · Sửa hai họ lỗi có ảnh hưởng lớn nhất

- **0–10 phút.** Chọn một lỗi xuất hiện ở nhiều câu và một lỗi đã lặp ở nhiều buổi. Ưu tiên lỗi làm sai cả bài, như nhầm trục, khóa ghép, mẫu số metric hoặc thứ tự fit.
- **10–30 phút.** Làm lại mỗi câu đại diện từ giấy trắng. Nếu kẹt, mở đúng đoạn ghi chú cần thiết, đóng lại rồi viết quy trình giải bằng lời của mình.
- **30–60 phút.** Làm hai biến thể mới cho mỗi họ. Đổi đúng một yếu tố ở câu đầu, chẳng hạn khóa lặp hoặc lớp dương. Trộn hai họ với câu khác ở lượt cuối để luyện nhận dạng dạng bài.
- **60–75 phút.** Chốt quy tắc, dấu hiệu nhận biết và một ca biên. Nếu vẫn sai ở biến thể, đưa họ đó vào Buổi 15.

### Buổi 14 · Đề thử B

- **0–40 phút.** Làm Đề B với điều kiện giống Đề A. Ghi dấu câu phải quay lại và câu chọn bằng dự đoán.
- **40–55 phút.** Chấm điểm. Đối chiếu ba số với Đề A: điểm, câu chắc đúng và số câu chưa xử lý đúng thời gian. Mục tiêu tham chiếu là 20/24 câu.
- **55–75 phút.** Chọn hai câu tái phạm và một câu mất nhiều thời gian. Giải lại trên giấy trắng và xác định khi nào cần đọc lại đề, đổi cách trace hoặc bỏ qua tạm thời.

## Ngày 8 · Bù các lỗi còn tồn đọng

### Buổi 15 · Kiểm tra lại sau một quãng nghỉ

- **0–15 phút.** Viết từ trí nhớ công thức hoặc quy tắc của tối đa hai họ yếu, rồi đối chiếu ghi chú. Kiểm tra cả mẫu số, trục và điều kiện áp dụng.
- **15–45 phút.** Làm 8–10 câu mới đan xen hai họ yếu với một họ đã vững. Không xem nhãn họ trước khi giải nếu đang có sẵn danh sách câu hỗn hợp.
- **45–65 phút.** Lấy một lỗi từ đề và thay hai chi tiết trong đề bài. Ví dụ, thay kiểu nối và thêm khóa lặp, hoặc đổi lớp dương và tăng chi phí bỏ sót.
- **65–75 phút.** Kiểm tra đầu ra. Mục tiêu ít nhất 80% câu chắc đúng. Nếu vẫn sai cùng cơ chế, giữ lại đúng họ này để làm tiếp sau mốc kiểm tra cuối.

## Ngày 9 · Kiểm tra thành thạo

### Buổi 16 · Một lượt hỗn hợp và một bài thực hành độc lập

- **0–25 phút.** Làm 12 câu mới trải trên ít nhất bốn chương, gồm đọc code, tính tay, phân tích bảng và chọn phương pháp. Ghi chắc hoặc đoán trước khi chấm.
- **25–55 phút.** Làm một bài từ tệp thô đến một biểu đồ có chú thích hoặc một kết quả đánh giá mô hình. Tự giải thích các bước kiểm tra schema, số dòng/shape, khóa ghép hoặc cách chia train/test.
- **55–75 phút.** So với mục tiêu: 10/12 câu chắc đúng, giải thích được một ca biên và tự hoàn thành bài liên chương. Ghi tối đa ba họ chưa đạt, kèm một câu mới và mốc kiểm tra sau 1, 3 hoặc 7 ngày.

## Theo dõi và điều chỉnh

- **Tính câu chắc đúng.** Chỉ tính câu có đáp án đúng ngay lần đầu và giải thích được quy tắc. Ghi riêng câu đúng do đoán để đưa vào lượt ôn.
- **Chọn lỗi cần sửa.** Ưu tiên lỗi lặp từ hai lần, làm sai cả quy trình hoặc xuất hiện ở nhiều chương. Ghi mã câu, bước đầu tiên lệch, quy tắc đúng, một biến thể và mốc thử lại.
- **Ôn sau 1, 3 và 7 ngày.** Lần đầu giải lại câu đại diện. Lần sau làm câu mới cùng họ. Lần cuối trộn với họ khác và tự nhận dạng cách giải. Nếu sai lại, tính lượt ôn tiếp từ lần chữa đó.
- **Chuyển sang phần tiếp theo.** Khi đạt ít nhất 80% câu chắc đúng và tự giải thích được một ca biên, chuyển buổi. Nếu chưa đạt, lấy 20 phút đầu buổi kế tiếp cho đúng một họ yếu. Nếu gặp lỗi tiên quyết khiến không làm được bài sau, dùng Buổi 15 hoặc thêm một buổi riêng để bù.

## Sơ đồ tuyến học

[![Tuyến học 8 chương](../../diagrams/00%20%C4%90i%E1%BB%81u%20h%C6%B0%E1%BB%9Bng/Tuy%E1%BA%BFn%20h%E1%BB%8Dc%208%20ch%C6%B0%C6%A1ng.excalidraw.svg)](../../diagrams/00%20%C4%90i%E1%BB%81u%20h%C6%B0%E1%BB%9Bng/Tuy%E1%BA%BFn%20h%E1%BB%8Dc%208%20ch%C6%B0%C6%A1ng.excalidraw.md)

## Mục lục 8 chương

1. [Tổng quan](../01%20T%E1%BB%95ng%20quan/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
2. [Python](../02%20Python/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
3. [NumPy và Pandas](../03%20NumPy%20v%C3%A0%20Pandas/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
4. [Nhập và lưu trữ](../04%20Nh%E1%BA%ADp%20v%C3%A0%20l%C6%B0u%20tr%E1%BB%AF/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
5. [Làm sạch](../05%20L%C3%A0m%20s%E1%BA%A1ch/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
6. [Ghép và biến đổi](../06%20Gh%C3%A9p%20v%C3%A0%20bi%E1%BA%BFn%20%C4%91%E1%BB%95i/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
7. [Trực quan hóa](../07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
8. [Học máy có giám sát](../08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/00%20M%E1%BB%A5c%20l%E1%BB%A5c.md)
