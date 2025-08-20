# Predicting Cefepime Resistance in *E. coli* Using Genomic Data

## 📌 Project Overview
This project trains and evaluates two machine learning models — **Logistic Regression** and **Random Forest** — to predict *Escherichia coli* resistance to **cefepime**, a fourth-generation cephalosporin antibiotic.

The dataset contains:
- **Presence/absence gene features**
- **k-mer counts** (common genomic bioinformatics format)
- Labels for **Resistant (R)** or **Susceptible (S)** isolates

After evaluation, the **Random Forest** model was chosen due to:
- Strong **recall** (important for minimizing false negatives in resistance detection)
- **Interpretability** via feature importance

---

## 📂 Data Description

| File | Description |
|------|-------------|
| `train_pa_genes.csv` / `test_pa_genes.csv` | Gene presence/absence matrices |
| `train_kmers.npy` / `test_kmers.npy` | k-mer feature arrays |
| `y_train.npy` | Training labels (R/S) |
| `train_ids.npy` / `test_ids.npy` | Genome IDs |
| `train_genes.csv` | Gene alignment metadata (optional) |

---

## 🛠 Methods

1. **Data Loading & Preprocessing**
   - Load genomic features (presence/absence & k-mers)
   - Align genome IDs and labels
   - Apply scaling for Logistic Regression

2. **Model Training**
   - Baseline: Logistic Regression & Random Forest (default settings)
   - Nested Cross-Validation with `GridSearchCV` for hyperparameter tuning
   - Stratified folds to maintain class balance

3. **Evaluation Metrics**
   - **Balanced Accuracy** (handles class imbalance)
   - **Confusion Matrix**
   - **Classification Report** (precision, recall, F1-score)

4. **Model Selection**
   - Compared tuned Logistic Regression vs. tuned Random Forest
   - Selected Random Forest for final model

---

## 📊 Key Results
- **Logistic Regression** achieved higher balanced accuracy and recall than Random Forest.
- Feature importance revealed specific genes strongly associated with cefepime resistance.
- Nested CV ensured no data leakage and reliable performance estimates.

---

## 📦 Dependencies

Install required packages:
```bash
pip install numpy pandas matplotlib scikit-learn scipy
