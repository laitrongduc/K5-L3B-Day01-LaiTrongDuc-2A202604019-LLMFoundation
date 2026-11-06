# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV:** 2A202604019
- **Họ và tên:** LẠI TRỌNG ĐỨC
- **SEED** (in ở ô đầu notebook): 786

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | ☐ |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | ☐ |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | ☐ |

## 2. Kết quả chính

*Chép bảng so sánh cuối Phần 5 (F1 test, F1 SUB 40, p95 ms/tin, USD/1k tin) của chính bạn.*
                                 precision  recall  F1 (test)  F1 (SUB 40)  \
1. BoW + LogReg (tự code)            0.987   0.848      0.912        0.857   
2. BoW + MLP (deep learning)         0.988   0.913      0.949        0.947   
3a. Encoder (MiniLM) + kNN           0.870   0.946      0.906        0.952   
3b. Encoder (MiniLM) + LogReg        0.935   0.935      0.935        0.974   
3c. Encoder (MiniLM) + MLP head      0.956   0.935      0.945        0.974   
4c. LLM nhỏ few-shot                 1.000   0.900      0.947        0.947   

                                 train (s)  tin/s (cả lô)  p50 ms/tin  \
1. BoW + LogReg (tự code)            5.547      17398.747       0.050   
2. BoW + MLP (deep learning)        11.566      17299.308       0.316   
3a. Encoder (MiniLM) + kNN          89.486         19.510      75.776   
3b. Encoder (MiniLM) + LogReg       89.908         57.309      25.706   
3c. Encoder (MiniLM) + MLP head     90.506         52.270      24.984   
4c. LLM nhỏ few-shot                 0.000          0.970     965.935   

                                 p95 ms/tin  USD / 1k tin  
1. BoW + LogReg (tự code)             0.071         0.000  
2. BoW + MLP (deep learning)          0.742         0.000  
3a. Encoder (MiniLM) + kNN          123.441         0.000  
3b. Encoder (MiniLM) + LogReg        36.725         0.000  
3c. Encoder (MiniLM) + MLP head      37.233         0.000  
4c. LLM nhỏ few-shot               1419.131         0.023  
• Hàng LLM chỉ đo trên SUB (40 tin) → so sánh chất lượng công bằng bằng cột 'F1 (SUB 40)'.
• SUB chỉ 40 tin: 1 tin sai đổi F1 vài điểm. Chênh < ~0.05 F1 coi như HOÀ — đừng xếp hạng theo số lẻ.
• Inference đo TỪ VĂN BẢN THÔ → NHÃN (gồm cả vectorize / encode). p50/p95 = gọi từng tin một, như một request thật.
• train (s) của 3a/3b/3c = thời gian encoder MiniLM encode tập train (+ train đầu LogReg / MLP); LLM = 0 vì không train. Số đo phụ thuộc CPU/GPU của Colab.


## 3. Dự đoán và thực tế

*Chọn 3 dự đoán `predict(...)` lệch nhiều nhất so với kết quả. Mỗi cái: bạn đoán gì, ra gì, vì sao lệch.*

## 4. Phân tích 50 case khó

*Model nào tụt nhiều nhất, ở nhóm case nào? Nêu 2 case cụ thể và cơ chế khiến model sai.*

## 5. Thử thách cá nhân

*Đề theo SEED của bạn, cách làm, kết quả, giải thích.*

## 6. Phương án cho sản phẩm thật

*Với yêu cầu p95 < 50 ms/tin cho 10 triệu SMS/ngày: chọn phương án nào, dẫn số liệu nào, chấp nhận đánh đổi gì.*

## 7. AI log và điều đã học

*Mỗi lần dùng AI: hỏi gì, nhận gì, bạn sửa gì. Sau đó 2–3 câu: điều bạn hiểu ra hôm nay mà trước đó chưa hiểu.*
