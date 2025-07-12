# Random-Forest_on_Titanic_Datasets
# 🛳️ Titanic Survival Prediction

This project builds and compares machine learning models (Random Forest and XGBoost) to predict passenger survival from the Titanic dataset. It includes professional preprocessing, model training, evaluation, and performance visualization.

---

## 📦 Dataset

- **Source**: [Kaggle Titanic: Machine Learning from Disaster](https://www.kaggle.com/c/titanic/data)
- **Files Used**:
  - `train.csv`: Training dataset (with `Survived` label)
  - `test.csv`: Test dataset (for inference only)

---

## 📊 Features Used

- `Pclass` (Ticket class)
- `Sex`
- `Age` (Imputed)
- `SibSp` (Siblings/Spouses aboard)
- `Parch` (Parents/Children aboard)
- `Fare`
- `Embarked`
- `Title` (extracted from `Name`)

> 🧹 **Dropped**: `PassengerId`, `Name`, `Ticket`, `Cabin` after extracting useful info.

---

## 🧪 Data Preprocessing

- Handled missing values:
  - `Age`: Imputed by median per (`Pclass`, `Sex`)
  - `Embarked`: Mode
  - `Fare` (test set): Median
- Extracted `Title` from `Name` and grouped rare titles
- Applied **Label Encoding** / **One-Hot Encoding** on categorical variables
- Feature scaling was **not required** due to tree-based models

---

## 🤖 Models Used

### 1. Random Forest Classifier
- `n_estimators=100`
- `class_weight='balanced'`
- Handles feature interactions well

### 2. XGBoost Classifier
- `n_estimators=100`
- `learning_rate=0.1`
- `max_depth=3`
- `scale_pos_weight` (for class imbalance tuning)
- Optimized for better recall on minority class (Survived)

---

## ⚙️ Model Evaluation (on validation set)

| Metric              | Random Forest | XGBoost |
|---------------------|----------------|----------|
| **Accuracy**        | 83.76%         | **85.47%** |
| **Precision (1)**   | 76.67%         | **82.14%** |
| **Recall (1)**      | 65.71%         | 65.71% |
| **F1 Score (1)**    | 70.77%         | **73.01%** |
| **Confusion Matrix**| `[[75, 7], [12, 23]]` | `[[7]()]()
