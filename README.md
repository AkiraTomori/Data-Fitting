# Dự Án 3: Dự Đoán Bệnh Tim Bằng Hồi Quy Logistic

**MSSV:** 23127379

## Mô Tả Dự Án

Dự án này thực hiện phân tích và dự đoán bệnh tim mạch sử dụng mô hình **Logistic Regression** được xây dựng từ đầu (from scratch) bằng thuật toán Gradient Descent. Dự án bao gồm việc khám phá dữ liệu, xây dựng mô hình đơn biến và đa biến, cùng với đánh giá hiệu năng chi tiết.

## Cấu Trúc Thư Mục

```
📦 Do an 3
├── 📄 23127379.ipynb          # Notebook chính chứa code và phân tích
├── 📄 train.csv               # Dữ liệu huấn luyện (248 mẫu)
└── 📄 README.md               # File này
```

## Dữ Liệu

### Dataset: Heart Disease Prediction
- **Số mẫu:** 248 bệnh nhân
- **Số đặc trưng:** 13 đặc trưng y học
- **Biến mục tiêu:** `target` (0 = không bệnh, 1 = có bệnh)

### Các Đặc Trưng

| Tên Cột | Mô Tả |
|---------|-------|
| `age` | Tuổi của bệnh nhân |
| `sex` | Giới tính (0 = nữ, 1 = nam) |
| `cp` | Loại đau ngực (1-4) |
| `trestbps` | Huyết áp lúc nghỉ (mm Hg) |
| `chol` | Cholesterol huyết thanh (mg/dl) |
| `fbs` | Đường huyết lúc đói > 120 mg/dl (0 = không, 1 = có) |
| `restecg` | Kết quả điện tâm đồ lúc nghỉ (0-2) |
| `thalach` | Nhịp tim tối đa đạt được |
| `exang` | Đau thắt ngực do gắng sức (0 = không, 1 = có) |
| `oldpeak` | Độ suy giảm ST do gắng sức so với nghỉ |
| `slope` | Độ dốc của đoạn ST đỉnh khi gắng sức (1-3) |
| `ca` | Số mạch máu chính được nhuộm màu bởi huỳnh quang (0-3) |
| `thal` | Thalassemia (3 = bình thường, 6 = khuyết tật cố định, 7 = khuyết tật có thể khắc phục) |
| `target` | Có bệnh tim hay không (0 = không, 1 = có) |

## Nội Dung Dự Án

### Phần 1: Mô Hình Hồi Quy Đơn Biến

1. **Khám phá dữ liệu:**
   - Phân tích mối liên hệ giữa chỉ số đường huyết (`fbs`) và bệnh tim
   - Phân tích mối liên hệ giữa tuổi (`age`) và bệnh tim
   - Tạo bảng chéo và biểu đồ trực quan

2. **Xây dựng mô hình:**
   - Huấn luyện mô hình Logistic Regression với biến `fbs`
   - Diễn giải các hệ số $e^{\beta_0}$ và $e^{\beta_1}$
   - Tính xác suất dự đoán cho từng trường hợp

3. **Đánh giá mô hình:**
   - Confusion Matrix
   - Accuracy, Precision, Recall, F1-Score
   - ROC Curve và AUC Score

### Phần 2: Mô Hình Hồi Quy Đa Biến

4. **Xây dựng mô hình đầy đủ:**
   - Huấn luyện với 13 đặc trưng
   - Viết công thức mô hình tổng quát
   - Bảng hệ số hồi quy với kiểm định thống kê

5. **Phân tích thống kê:**
   - Xác định biến có ý nghĩa thống kê (p-value < 0.05)
   - So sánh Log-Likelihood giữa mô hình đơn biến và đa biến

6. **Đánh giá và so sánh:**
   - Cross-validation với K-Fold
   - So sánh hiệu năng trên tập train, validation và test
   - Phân tích ROC-AUC

## Công Nghệ Sử Dụng

### Thư Viện Python

```python
numpy           # Tính toán số học
pandas          # Xử lý dữ liệu
matplotlib      # Vẽ biểu đồ
seaborn         # Trực quan hóa thống kê
scikit-learn    # Chia dữ liệu, metrics
statsmodels     # Kiểm định thống kê (để so sánh)
scipy           # Tính p-value
```

### Mô Hình Tự Xây Dựng

- **LogisticRegression Class:** Mô hình Logistic Regression được implement hoàn toàn từ đầu
  - Sử dụng Gradient Descent để tối ưu hóa
  - Hỗ trợ chuẩn hóa dữ liệu (z-score scaling)
  - Tính toán các metrics: loss, accuracy, ROC-AUC
  - Kiểm định thống kê: z-score, p-value

## Cài Đặt và Chạy

### Yêu Cầu Hệ Thống

- Python 3.8+
- Jupyter Notebook hoặc VS Code với extension Python

### Cài Đặt Thư Viện

```bash
pip install numpy pandas matplotlib seaborn scikit-learn statsmodels scipy
```

### Chạy Dự Án

1. Clone hoặc tải về thư mục dự án
2. Mở file `23127379.ipynb` bằng Jupyter Notebook hoặc VS Code
3. Chạy các cell theo thứ tự từ trên xuống

## Kết Quả Chính

### Mô Hình Đơn Biến (fbs)
- **Đặc trưng:** Chỉ số đường huyết (fbs)
- **Test Accuracy:** ~54-60%
- **AUC:** ~0.50-0.55
- **Nhận xét:** Hiệu năng thấp, biến fbs không đủ để dự đoán bệnh tim

### Mô Hình Đa Biến (13 đặc trưng)
- **Đặc trưng:** Tất cả 13 biến y học
- **Test Accuracy:** ~85-90%
- **AUC:** ~0.90-0.95
- **Nhận xét:** Hiệu năng cao hơn đáng kể so với mô hình đơn biến

### Các Biến Quan Trọng Nhất (p < 0.05)
Các biến có ý nghĩa thống kê được xác định thông qua kiểm định z-test và p-value.

## Hạn Chế và Hướng Cải Tiến

### Hạn Chế
1. **Giả định tuyến tính:** Logistic Regression giả định mối quan hệ tuyến tính giữa log-odds và các đặc trưng
2. **Không xử lý tương tác:** Mô hình không tự động học được tương tác giữa các biến
3. **Dữ liệu nhỏ:** Chỉ có 248 mẫu, có thể dẫn đến overfitting
4. **Multicollinearity:** Một số biến có thể tương quan cao với nhau

### Hướng Cải Tiến
1. **Feature Engineering:** Thêm các biến tương tác, polynomial features
2. **Regularization:** Thêm L1/L2 regularization để tránh overfitting
3. **Ensemble Methods:** Thử nghiệm Random Forest, Gradient Boosting
4. **Deep Learning:** Sử dụng Neural Network cho các mối quan hệ phức tạp hơn
5. **Xử lý imbalanced data:** Áp dụng SMOTE hoặc class weighting nếu dữ liệu mất cân bằng

## Tài Liệu Tham Khảo

- [Logistic Regression từ đầu - YouTube](https://www.youtube.com/watch?v=S6iuhdYsGC8)
- [Logistic Regression Theory - GitHub](https://github.com/JuzerShakir/Logistic_Regression/blob/master/README.md)
- Statsmodels Documentation
- Scikit-learn Documentation

## Tác Giả

**Sinh viên:** Thái Minh Huy
**Môn học:** Phương Pháp Tính (PPT)  
**Học kỳ:** 3 - Năm 2  
**Trường:** VNU-HCMUS

## License

Dự án này được tạo ra cho mục đích học tập.

---

*Cập nhật lần cuối: Tháng 1/2026*