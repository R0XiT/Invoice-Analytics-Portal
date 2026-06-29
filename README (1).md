# 📦 Invoice Analytics Portal

An end-to-end Machine Learning application for **Freight Cost Prediction** and **Invoice Risk Assessment**, built using **Python, Scikit-learn, SQLite, and Streamlit**.

🚀 **Live Demo:** *Add your Streamlit URL here*
📂 **Repository:** *Add your GitHub repository URL here*

---

## 📌 Overview

Invoice Analytics Portal helps finance teams automate invoice analysis by combining machine learning with business rules.

The application provides two intelligent modules:

- 🚚 **Freight Cost Prediction**
- 🚨 **Invoice Manual Approval Flagging**

Instead of manually reviewing thousands of invoices, the system predicts freight costs and automatically identifies invoices that may require manual approval due to abnormal patterns.

---

## ✨ Features

### 🚚 Freight Cost Prediction

Predicts the expected freight cost for an invoice using:

- Quantity
- Invoice Amount (Dollars)

This assists with:

- Budget planning
- Cost forecasting
- Vendor negotiations
- Freight estimation

---

### 🚨 Invoice Risk Assessment

Predicts whether an invoice should be sent for **manual approval**.

The classifier analyzes features such as:

- Invoice Quantity
- Invoice Dollars
- Freight Cost
- Total Item Quantity
- Total Item Dollars

Invoices identified as risky are flagged for manual review.

---

## 🏗️ Project Architecture

```
Invoice Analytics Portal
│
├── app.py                         # Streamlit UI
│
├── freight_cost_prediction/
│   ├── train.py
│   ├── data_preprocessing.py
│   └── modeling_evaluation.py
│
├── invoice_flagging/
│   ├── train.py
│   ├── data_preprocessing.py
│   └── modeling_evaluation.py
│
├── inference/
│   ├── predict_freight.py
│   └── predict_invoice_flag.py
│
├── models/
│   ├── predict_freight_model.pkl
│   ├── predict_flag_invoice.pkl
│   └── scaler.pkl
│
├── data/
│   └── inventory.db
│
├── requirements.txt
└── README.md
```

---

## 🤖 Machine Learning Pipeline

### Freight Cost Prediction

**Task:** Regression

**Input Features**

| Feature | Description |
|---|---|
| Quantity | Number of units in the invoice |
| Invoice Dollars | Total invoice amount in USD |

**Models Evaluated & Results**

| Model | MAE | RMSE | R² Score |
|---|---|---|---|
| ✅ **Linear Regression** *(selected)* | **24.11** | **124.72** | **96.99%** |
| Decision Tree Regressor | 38.12 | 138.25 | 96.30% |
| Random Forest Regressor | 26.13 | 134.79 | 96.48% |

Linear Regression achieved the best MAE and R² score and is saved for inference.

---

### Invoice Manual Approval Flagging

**Task:** Binary Classification

**Target Variable**

Invoices are labeled using business rules based on:

- Difference between invoice amount and item total
- Average receiving delay

**Input Features**

| Feature | Description |
|---|---|
| Invoice Quantity | Number of units |
| Invoice Dollars | Total invoice amount |
| Freight | Freight cost |
| Total Item Quantity | Sum of all item quantities |
| Total Item Dollars | Sum of all item costs |

**Model**

- Random Forest Classifier

**Hyperparameter Tuning**

GridSearchCV was used to optimize:

- Number of estimators
- Maximum tree depth
- Split criterion
- Minimum samples per split
- Minimum samples per leaf

**Model Performance**

| Metric | Value |
|---|---|
| Accuracy | 89% |
| Macro Avg Precision | 0.91 |
| Macro Avg Recall | 0.85 |
| Macro Avg F1 Score | 0.87 |

**Classification Report**

| Class | Precision | Recall | F1-Score | Support |
|---|---|---|---|---|
| 0 (No Flag) | 0.87 | 0.98 | 0.92 | 725 |
| 1 (Flag) | 0.95 | 0.71 | 0.82 | 384 |
| **Weighted Avg** | **0.90** | **0.89** | **0.88** | **1109** |

---

## 📊 Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core language |
| Pandas | Data manipulation |
| NumPy | Numerical computing |
| SQLite | Data storage |
| Scikit-learn | ML models & evaluation |
| Joblib | Model serialization |
| Streamlit | Web UI |

---

## 💻 Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/Invoice-Analytics-Portal.git
```

Move into the project directory:

```bash
cd Invoice-Analytics-Portal
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
streamlit run app.py
```

---

## 🎯 Business Impact

| Benefit | Description |
|---|---|
| 📉 Cost Forecasting | Improved freight cost prediction accuracy |
| 🚨 Risk Detection | Early identification of abnormal invoices |
| 📄 Reduced Manual Work | Fewer invoices requiring manual verification |
| ⚡ Faster Operations | Streamlined finance workflows |
| 💰 Cost Visibility | Better insight into freight and invoice costs |

---

## 📷 Application Preview

> Add screenshots of:
> - Home Page
> - Freight Cost Prediction
> - Invoice Risk Prediction

---

## 🔮 Future Improvements

- [ ] Explainable AI using SHAP
- [ ] Model monitoring dashboard
- [ ] Cloud database integration
- [ ] User authentication
- [ ] Batch invoice prediction
- [ ] REST API deployment using FastAPI

---

## 👨‍💻 Author

**Rohit Ranjan**

B.Tech, Mechanical Engineering — Indian Institute of Technology Indore

*Interested in Machine Learning, Data Analytics, and Backend Development.*

---

## ⭐ Support

If you found this project useful, please consider giving the repository a ⭐ on GitHub!
