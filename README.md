🕵️ Fraudulent Transactions Detection
📌 Project Overview

This project uses a fraudulent transactions dataset to detect suspicious activities such as unauthorized transfers and cash-outs. Fraudulent agents typically drain customer accounts and attempt to cash out quickly. The goal of this project is to:

Build a machine learning model to detect fraud proactively

Identify the key factors that indicate fraud

Provide business insights and prevention strategies

📂 Dataset Description

step: Time unit (1 step = 1 hour, total = 744 steps ≈ 30 days)

type: Transaction type → CASH-IN, CASH-OUT, DEBIT, PAYMENT, TRANSFER

amount: Transaction amount

nameOrig: ID of customer initiating transaction

oldbalanceOrg / newbalanceOrig: Sender’s balance before & after transaction

nameDest: ID of recipient

oldbalanceDest / newbalanceDest: Recipient’s balance before & after transaction (not available for merchants "M...")

isFraud: 1 if transaction is fraud, 0 otherwise

isFlaggedFraud: Transactions flagged for illegal transfers (>200,000)

🛠️ Project Workflow
1. Data Cleaning

Removed irrelevant IDs (nameOrig, nameDest)

Encoded categorical variable type using One-Hot Encoding

Checked missing values, outliers, and multi-collinearity

Balanced dataset using SMOTE to handle fraud class imbalance

2. Exploratory Data Analysis (EDA)

Distribution of fraud vs non-fraud transactions

Fraud occurrences by transaction type

Correlation between balances and fraud

3. Feature Engineering

Created balance difference features:

diffOrig = oldbalanceOrg - newbalanceOrig

diffDest = newbalanceDest - oldbalanceDest

Selected meaningful variables for modeling

4. Modeling

Baseline: Logistic Regression

Advanced: Random Forest Classifier

Metrics Used: Precision, Recall, F1-score, Confusion Matrix

5. Insights

Most fraud occurs in TRANSFER and CASH-OUT transactions

Fraudsters often drain accounts completely (balance differences = strong signal)

isFlaggedFraud only detects very large transfers (>200k) → not enough by itself

📊 Results

Random Forest performed best with higher recall (catching more fraud cases)

Key features: transaction type, transaction amount, sender/receiver balance differences

🔑 Business Recommendations

Preventive Measures:

Real-time anomaly detection

Set transaction thresholds

Strengthen multi-factor authentication

Monitoring:

Track fraud detection rates

Compare losses before & after implementation

Monitor false positives to avoid customer inconvenience

🚀 How to Run the Project

Clone the repo or upload files to Google Colab

Install dependencies:

pip install imbalanced-learn


Upload dataset (fraudulent_transactions_data.csv)

Run the notebook cells step by step

View fraud detection results & insights

📌 Future Improvements

Use XGBoost/LightGBM for better fraud classification

Implement real-time streaming detection (Kafka + Spark)

Build an interactive dashboard (Streamlit/Power BI)

✨ This project demonstrates how data science can fight financial fraud and protect customers in real-world systems.
