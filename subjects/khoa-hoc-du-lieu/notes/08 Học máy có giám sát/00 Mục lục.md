# Chương 08 · Học máy có giám sát

> **abstract** Chương này trả lời gì?
> Làm sao **dạy máy dự đoán từ dữ liệu có nhãn**: chia train/test, dùng 5 mô hình (Linear, Logistic, KNN, cây, rừng) cho **hồi quy** và **phân loại**, tính tay một dự đoán, rồi chọn **chỉ số đánh giá** đúng (RMSE, MAE, R², Precision, Recall, F1, AUC).
>
> **Đầu ra.** Nhận diện bài toán theo nhãn, chia dữ liệu đúng, tính tay dự đoán của từng mô hình trên bộ dữ liệu slide và chọn chỉ số theo chi phí lỗi.

## Thứ tự đọc

1. [01 Chương 08 - Train test và rò rỉ](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) · khái niệm ML, 3 loại học, train/test, quá khớp, quy trình, scikit-learn.
2. [03 Chương 08 - Hồi quy và KNN](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md) · Linear, KNN, cây, rừng trên dữ liệu lương; so sánh RMSE.
3. [04 Chương 08 - Logistic cây và rừng](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md) · Logistic, KNN, cây (Gini), rừng trên dữ liệu Đạt/Trượt.
4. [08 Chương 08 - Điều kiện dừng và chuẩn hóa](08%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%C3%B3a.md) · khi nào dừng học, khi nào cần scale.
5. [05 Chương 08 - Ma trận nhầm lẫn và chỉ số](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md) · MAE, R², ma trận nhầm lẫn, P/R/F1, ROC–AUC.
6. [06 Chương 08 - Công thức và cú pháp](06%20Ch%C6%B0%C6%A1ng%2008%20-%20C%C3%B4ng%20th%E1%BB%A9c%20v%C3%A0%20c%C3%BA%20ph%C3%A1p.md) · bảng tra công thức và API.
7. [07 Chương 08 - Tự kiểm tra](07%20Ch%C6%B0%C6%A1ng%2008%20-%20T%E1%BB%B1%20ki%E1%BB%83m%20tra.md) → Thẻ nhớ chương 8 (thẻ nhớ `#flashcards/chuong-8`).
8. Luyện thêm: [Thực hành thêm - Tính điểm chia cây và đọc rừng](Th%E1%BB%B1c%20h%C3%A0nh%20th%C3%AAm%20-%20T%C3%ADnh%20%C4%91i%E1%BB%83m%20chia%20c%C3%A2y%20v%C3%A0%20%C4%91%E1%BB%8Dc%20r%E1%BB%ABng.md).

## Bản đồ chương



**Sơ đồ Excalidraw:** [02 Luồng train test.excalidraw](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/02%20Lu%E1%BB%93ng%20train%20test.excalidraw.md) · [Cây hồi quy chọn ngưỡng 4.5.excalidraw](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/C%C3%A2y%20h%E1%BB%93i%20quy%20ch%E1%BB%8Dn%20ng%C6%B0%E1%BB%A1ng%204.5.excalidraw.md) · [Bốn mô hình dự đoán x bằng 7.excalidraw](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/B%E1%BB%91n%20m%C3%B4%20h%C3%ACnh%20d%E1%BB%B1%20%C4%91o%C3%A1n%20x%20b%E1%BA%B1ng%207.excalidraw.md) · [Ma trận nhầm lẫn và bốn chỉ số.excalidraw](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20b%E1%BB%91n%20ch%E1%BB%89%20s%E1%BB%91.excalidraw.md) · [Chọn chuẩn hóa và điều kiện dừng.excalidraw](../../diagrams/08%20H%E1%BB%8Dc%20m%C3%A1y%20c%C3%B3%20gi%C3%A1m%20s%C3%A1t/Ch%E1%BB%8Dn%20chu%E1%BA%A9n%20h%C3%B3a%20v%C3%A0%20%C4%91i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng.excalidraw.md)

## Phủ slide

| Trang | Chủ đề | Note |
| --- | --- | --- |
| 1–5 | Bìa, mục lục bài giảng và mục 8.1 | Không có nội dung thi |
| 6–7 | Khái niệm ML, ví dụ email spam | [01 · mục 1](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) |
| 8–9 | Ba loại học máy | [01 · mục 2](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) |
| 10–11 | Hồi quy và phân loại, bảng 5 mô hình | [01 · mục 3](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) |
| 12–13 | Quy tắc chia train/test | [01 · mục 4](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) |
| 14–15 | MSE, RMSE, Accuracy | [01 · mục 5](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) |
| 16–17 | Quá khớp, dưới khớp | [01 · mục 6](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) |
| 18–20 | Quy trình dự án, 3 bước scikit-learn | [01 · mục 7](01%20Ch%C6%B0%C6%A1ng%2008%20-%20Train%20test%20v%C3%A0%20r%C3%B2%20r%E1%BB%89.md) |
| 21–26 | Mục lục 8.2, bài toán hồi quy, dữ liệu lương, code khởi tạo | [03 · mục 1](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md) |
| 27–31 | Linear Regression | [03 · mục 2](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md) |
| 32–37 | KNN hồi quy | [03 · mục 3](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md) |
| 38–45 | Decision Tree hồi quy (MSE, ngưỡng 4.5) | [03 · mục 4](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md) |
| 46–52 | Random Forest hồi quy | [03 · mục 5](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md) |
| 53–55 | So sánh RMSE 4 mô hình | [03 · mục 6](03%20Ch%C6%B0%C6%A1ng%2008%20-%20H%E1%BB%93i%20quy%20v%C3%A0%20KNN.md) |
| 56–61 | Mục lục 8.3, bài toán phân loại, dữ liệu Đạt/Trượt | [04 · mục 1](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md) |
| 62–67 | Logistic Regression | [04 · mục 2](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md) |
| 68–73 | KNN phân loại | [04 · mục 3](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md) |
| 74–82 | Decision Tree phân loại, Gini | [04 · mục 4](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md) |
| 83–90 | Random Forest phân loại | [04 · mục 5](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md) |
| 91–93 | So sánh Accuracy 4 mô hình | [04 · mục 6](04%20Ch%C6%B0%C6%A1ng%2008%20-%20Logistic%20c%C3%A2y%20v%C3%A0%20r%E1%BB%ABng.md) |
| 94–95 | Điều kiện dừng học | [08 · mục 1](08%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%C3%B3a.md) |
| 96–97 | Chuẩn hóa dữ liệu | [08 · mục 2](08%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%C3%B3a.md) |
| 98–100 | Chỉ số nâng cao hồi quy: MAE, R² | [05 · mục 1](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md) |
| 101–102 | Vấn đề của Accuracy | [05 · mục 2](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md) |
| 103–104 | Ma trận nhầm lẫn | [05 · mục 3](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md) |
| 105 | Precision, Recall, F1 | [05 · mục 4](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md) |
| 106–107 | ROC và AUC | [05 · mục 5](05%20Ch%C6%B0%C6%A1ng%2008%20-%20Ma%20tr%E1%BA%ADn%20nh%E1%BA%A7m%20l%E1%BA%ABn%20v%C3%A0%20ch%E1%BB%89%20s%E1%BB%91.md) |
| 108–109 | Tóm tắt, tài liệu tham khảo | [08 · mục 3](08%20Ch%C6%B0%C6%A1ng%2008%20-%20%C4%90i%E1%BB%81u%20ki%E1%BB%87n%20d%E1%BB%ABng%20v%C3%A0%20chu%E1%BA%A9n%20h%C3%B3a.md) |
| 110 | Trang kết | Không có nội dung thi |

## Luyện theo họ bài

| Họ | Note lý thuyết |
| --- | --- |
| F801 Chia train-test | 01 |
| F802 Rò rỉ dữ liệu | 01, 08 |
| F803 Hồi quy tuyến tính | 03 |
| F804 Sai số hồi quy | 05 |
| F805 KNN | 03, 04 |
| F806 Logistic | 04 |
| F807 Cây quyết định | 03, 04 |
| F808 Rừng ngẫu nhiên | 03, 04 |
| F809 Ma trận nhầm lẫn | 05 |
| F810 Quá khớp | 01 |
| F811 Quy trình scikit-learn | 01, 06 |
| F812 EDA | 01 |

Bài mẫu có lời giải: các họ bài của chương 8.

**Cần biết trước.** Chuẩn hóa đặc trưng, dữ liệu thiếu và mã hóa phân loại. **Áp dụng ở.** So sánh lỗi hoặc kết quả phân loại bằng [01 Chương 07 - Chọn và đọc biểu đồ](../07%20Tr%E1%BB%B1c%20quan%20h%C3%B3a/01%20Ch%C6%B0%C6%A1ng%2007%20-%20Ch%E1%BB%8Dn%20v%C3%A0%20%C4%91%E1%BB%8Dc%20bi%E1%BB%83u%20%C4%91%E1%BB%93.md).

## Phân tích chuyên sâu

Tập 1.000 mẫu chỉ có 20 dương. Mô hình A dự đoán âm hết. Mô hình B bắt đúng 15 dương và báo nhầm 35 âm.

> **check** Lập luận và ca biên
> A đạt 98% accuracy và recall 0. B có recall 75%, precision 30% và accuracy 96%. Chọn theo chi phí bỏ sót và báo nhầm. Nếu điều chỉnh ngưỡng, đánh giá trên tập validation hoặc CV rồi dùng test cuối cùng. Fit mọi biến đổi trên train.
