# 🚨 Network Intrusion Detection using Machine Learning

## 📋 Giới thiệu

Hệ thống phát hiện xâm nhập mạng thời gian thực sử dụng bộ dữ liệu **CIC-IDS2017**.
Dự án áp dụng các kỹ thuật Machine Learning để phát hiện các loại tấn công mạng khác nhau.

---

## 🔗 Dataset

* CIC-IDS2017: [https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset](https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset)

---

## 🏗️ Project Architecture

```text
Raw Data → Preprocessing → Scaling → SMOTE + UnderSampling
        → Model Training → Evaluation → Best Model → Save (.pkl)
```

---

## 🚀 Cài đặt

```bash
git clone https://github.com/Hoc273/Network-Intrusion-Detection--ML.git
cd Network-Intrusion-Detection--ML
pip install -r requirements.txt
```

### 📦 Requirements

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
imbalanced-learn
joblib
```

---

## 📊 Kết quả So sánh 5 Mô hình

| Model               | Accuracy | Precision | Recall   | F1-Score | Time (s) |
| ------------------- | -------- | --------- | -------- | -------- | -------- |
| Logistic Regression | 66.71%   | 94.38%    | 66.71%   | 76.15%   | 219.2    |
| SVM (Linear)        | 73.78%   | 94.52%    | 73.78%   | 81.30%   | 225.5    |
| Naive Bayes         | 36.27%   | 96.62%    | 36.27%   | 49.72%   | 0.3      |
| KNN                 | 94.23%   | 97.67%    | 94.23%   | 95.60%   | 0.2      |
| Random Forest       | 98.51%   |  99.66%   |  98.51%  |  99.03%  | 36.1     |

> 🏆 **Best Model: Random Forest (F1-score = 99.03%)**

---

## ⚖️ Xử lý mất cân bằng dữ liệu

* SMOTE (Synthetic Oversampling)
* Random UnderSampling
  → Giúp cải thiện khả năng phát hiện các lớp tấn công hiếm.

---

## 📁 Cấu trúc Dự án

```bash
.
├── outputs/          # Biểu đồ EDA, confusion matrix
├── models/           # random_forest_ids.pkl
├── logs/             # alerts.log (optional)
├── notebook.ipynb    # Source code chính
└── requirements.txt
```

---

## 💾 Saved Model

Model tốt nhất (**Random Forest**) được lưu tại:

```bash
models/random_forest_ids.pkl
```

### 🔧 Cách sử dụng

```python
import joblib

model = joblib.load("models/random_forest_ids.pkl")
y_pred = model.predict(X_test)
```

> ⚠️ Lưu ý: Dữ liệu đầu vào cần được preprocessing giống như lúc training.

---

## 📦 Deliverables

* ✅ Source code (`.ipynb`)
* ✅ README.md (this file)
* ✅ Commit history (GitHub)
* ✅ Trained model (`.pkl`)
* ⚠️ Log file (`alerts.log`) – optional

---

## 👨‍💻 Author

* Nguyễn Lê Hoàng Học

---

👉 review luôn repo GitHub của bạn
👉 hoặc giúp bạn chỉnh README “level portfolio” (đẹp như project đi xin việc 😄)
