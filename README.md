# Credit Card Fraud Detection

Detecting fraudulent credit card transactions in a heavily imbalanced dataset, where fraud makes up only 0.17% of all transactions. Final project for the Data Science course at PTIT (team of 3).

## Dataset

[Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) from Kaggle:

- 284,807 transactions, 492 of them fraudulent (0.17%)
- Features `V1`–`V28` are PCA-transformed for confidentiality; `Time` and `Amount` are raw
- 9,144 duplicate rows removed, leaving 275,663 transactions

With this level of imbalance, accuracy is meaningless (predicting "not fraud" every time scores 99.8%), so models are compared on precision, recall, F1, ROC-AUC and PR-AUC.

## Approach

1. **EDA**: class distribution, outliers, correlation matrix, and how transaction amount differs between fraud and normal transactions
2. **Preprocessing**: scale `Amount`, drop `Time`, remove duplicates, stratified 80/20 train/test split
3. **Models**: Logistic Regression, Random Forest, XGBoost
4. **Evaluation**: classification report, confusion matrix, ROC and PR curves
5. **Further analysis**: threshold tuning, 5-fold stratified cross-validation, random undersampling

## Results

Fraud class (class 1) on the test set, 55,133 transactions with 95 frauds:

| Model | Precision | Recall | F1 |
|---|---|---|---|
| Logistic Regression | 0.84 | 0.66 | 0.74 |
| Random Forest | 1.00 | 0.78 | 0.88 |
| **XGBoost** | **0.97** | **0.80** | **0.88** |

- **Random Forest** almost never raises a false alarm, which suits cases where blocking a legitimate customer is costly.
- **XGBoost** catches the most fraud while keeping false alarms very low, giving the best overall balance.
- **Logistic Regression** is stable across folds (5-fold CV: ROC-AUC 0.979 ± 0.008, PR-AUC 0.742 ± 0.019) but misses about a third of fraud cases.

The full analysis and report (in Vietnamese) are in the notebook and the PDF.

## Team

| Member | Responsibilities |
|---|---|
| Nguyễn Thành Nam | Data loading, EDA, visualization, data insights |
| Sỳ Hưng | Preprocessing, pipeline, model training |
| Uông Ngọc Sơn | Model evaluation, threshold tuning, cross-validation, report |

## Run it

Requires Python 3.8+. Download `creditcard.csv` from Kaggle into the project folder, then:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn xgboost imbalanced-learn
jupyter notebook credit-card-fraud-detection-main-final.ipynb
```

## Files

- `credit-card-fraud-detection-main-final.ipynb`: full analysis and code
- `DoAn_KhoaHocDuLieu_CreditCardFraudDetection.pdf`: project report
