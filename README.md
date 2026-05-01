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
├── models/           # random_forest_ids.pkl, label_endcoder.pkl, scaler.pkl
├── logs/             # alerts.log (optional)
├── Network_IDS_ML.ipynb    # Source code chính
└── requirements.txt
```

---

## 💾 Saved Model

Model tốt nhất (**Random Forest**) được lưu tại:

```bash
models/random_forest_ids.pkl
```

## 🔧 Cách sử dụng

```python
import joblib
import pandas as pd

# 1. Load model + scaler + label encoder
model   = joblib.load("models/random_forest_ids.pkl")
scaler  = joblib.load("models/scaler.pkl")
le      = joblib.load("models/label_encoder.pkl")

# 2. Các đặc trưng cần thiết (18 features)
selected_features = [
    'Destination Port', 'Flow Duration',
    'Total Fwd Packets', 'Total Backward Packets',
    'Total Length of Fwd Packets', 'Total Length of Bwd Packets',
    'Fwd Packet Length Mean', 'Bwd Packet Length Mean',
    'Flow Bytes/s', 'Flow Packets/s',
    'Packet Length Mean', 'Packet Length Std',
    'SYN Flag Count', 'ACK Flag Count', 'FIN Flag Count',
    'RST Flag Count', 'PSH Flag Count', 'URG Flag Count'
]

# 3. Chuẩn bị dữ liệu
X = df[selected_features]
X_scaled = scaler.transform(X)

# 4. Dự đoán
y_pred_encoded = model.predict(X_scaled)
y_pred_label   = le.inverse_transform(y_pred_encoded)
print(y_pred_label)  # ['BENIGN', 'DDoS', ...]
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

* Nguyễn Lê Hoàng Học - N23DCCN158

---

