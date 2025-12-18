# Credit Card Fraud Detection  
## Đồ án cuối kỳ – Môn Khoa học dữ liệu

---

## 1. Thông tin chung

**Tên đề tài:**  
Phát hiện gian lận thẻ tín dụng (Credit Card Fraud Detection)

**Môn học:** Khoa học dữ liệu  
**Hình thức:** Đồ án nhóm  
**Số lượng thành viên:** 3

### Thành viên nhóm
- **Nguyễn Thành Nam** – N21DCCN150  
- **Sỳ Hưng** – N22DCCN138  
- **Uông Ngọc Sơn** – N22DCCI033  

---

## 2. Mục tiêu đề tài

Mục tiêu của đồ án là xây dựng và đánh giá các mô hình nhằm phát hiện các giao dịch gian lận thẻ tín dụng trong bối cảnh **dữ liệu mất cân bằng nghiêm trọng**.

Cụ thể, nhóm tập trung vào:
- Phân tích và khám phá dữ liệu (EDA)
- Xây dựng pipeline huấn luyện mô hình
- So sánh hiệu quả của nhiều mô hình khác nhau
- Đánh giá mô hình bằng các chỉ số phù hợp với bài toán gian lận
- Thực hiện các kỹ thuật nâng cao như threshold tuning và cross-validation

---

## 3. Mô tả tập dữ liệu

- **Nguồn dữ liệu:** Bộ dữ liệu Credit Card Fraud Detection (Kaggle)
- **Số lượng quan sát:** ~280.000 giao dịch
- **Số lượng đặc trưng:** 30
  - V1–V28: các đặc trưng đã được biến đổi bằng PCA
  - Amount: giá trị giao dịch
  - Class: nhãn mục tiêu (0 = hợp lệ, 1 = gian lận)

### Đặc điểm quan trọng
- Dữ liệu **mất cân bằng rất mạnh** (tỷ lệ gian lận < 0.2%)
- Do đó, các chỉ số như **Recall, Precision, F1-score, ROC-AUC, PR-AUC** được ưu tiên hơn Accuracy

---

## 4. Quy trình thực hiện

### 4.1. Khám phá dữ liệu (EDA)
- Kiểm tra phân phối dữ liệu
- Phân tích outliers
- Phân tích mối quan hệ giữa biến `Amount` và gian lận
- Kiểm tra ma trận tương quan (correlation matrix)

### 4.2. Tiền xử lý dữ liệu
- Tách đặc trưng và nhãn mục tiêu
- Chia dữ liệu train/test theo phương pháp phân tầng (stratified split)
- Chuẩn hóa biến `Amount` (khi sử dụng pipeline)

### 4.3. Huấn luyện mô hình
Nhóm huấn luyện và so sánh các mô hình sau:
- Logistic Regression
- Random Forest
- XGBoost

Quá trình huấn luyện được thực hiện thông qua phương thức `.fit()` trên tập train.

### 4.4. Đánh giá mô hình
Các mô hình được đánh giá bằng:
- Classification Report (Precision, Recall, F1-score)
- Confusion Matrix
- ROC Curve và ROC-AUC
- Precision–Recall Curve và PR-AUC

### 4.5. Đánh giá nâng cao
- **Threshold tuning** để tối ưu F1-score
- **So sánh metrics giữa các mô hình**
- **Cross-validation (StratifiedKFold)** cho Logistic Regression để đánh giá độ ổn định

---

## 5. Phân công nhiệm vụ

- **Nguyễn Thành Nam**
  - Nạp dữ liệu
  - Phân tích EDA
  - Trực quan hóa dữ liệu
  - Nhận xét insight từ dữ liệu

- **Sỳ Hưng**
  - Tiền xử lý dữ liệu
  - Xây dựng pipeline
  - Huấn luyện các mô hình Machine Learning

- **Uông Ngọc Sơn**
  - Đánh giá mô hình
  - Threshold tuning
  - Cross-validation
  - Tổng hợp kết quả và hoàn thiện báo cáo

---

## 6. Hướng dẫn chạy notebook

### Yêu cầu môi trường
- Python >= 3.8

### Cài đặt thư viện
```bash
pip install numpy pandas scikit-learn matplotlib seaborn xgboost


