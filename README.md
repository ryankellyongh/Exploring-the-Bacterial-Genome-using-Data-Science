# Predicting Cefepime Resistance in *E. coli* Using Genomic Data


## Introduction

Antimicrobial resistance (AMR) is one of the most serious public health threats worldwide.
Cefepime is a fourth-generation cephalosporin is widely used to treat Escherichia coli infections. However, rising resistance reduces treatment options and increases healthcare costs.
This project applies machine learning to genomic data to predict E. coli resistance to cefepime.
By modeling resistance patterns, this analysis contributes to early detection strategies and helps inform antibiotic stewardship programs.

## Project Overview
This project trains and evaluates two machine learning models — **Logistic Regression** and **Random Forest** — to predict *Escherichia coli* resistance to **cefepime**, a fourth-generation cephalosporin antibiotic.

The dataset contains:
- **Presence/absence gene features**
- **k-mer counts** (common genomic bioinformatics format)
- Labels for **Resistant (R)** or **Susceptible (S)** isolates

After evaluation, the **Logistic Regressiont** model was chosen due to:
- Higher balanced accuracy and recall (critical for minimizing false negatives in resistance detection)  
- Simplicity and interpretability  

---

## Data Description

| File | Description |
|------|-------------|
| `train_pa_genes.csv` / `test_pa_genes.csv` | Gene presence/absence matrices |
| `train_kmers.npy` / `test_kmers.npy` | k-mer feature arrays |
| `y_train.npy` | Training labels (R/S) |
| `train_ids.npy` / `test_ids.npy` | Genome IDs |
| `train_genes.csv` | Gene alignment metadata (optional) |

---

## Methods

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
   - Selected Logistic Regression for final model

---
## Results

| Model                       | Balanced Accuracy | Recall (Resistant) |
| --------------------------- | ----------------- | ------------------ |
| Random Forest (tuned)       | 0.817             | 0.733              |
| Logistic Regression (tuned) | **0.871**         | **0.867**          |


- **Logistic Regression** achieved higher balanced accuracy and recall than Random Forest.
- Feature importance revealed specific genes strongly associated with cefepime resistance.
- Nested CV ensured no data leakage and reliable performance estimates.

---

## Learnings & Takeaways
In this project, I gained hands-on experience working with genomic feature engineering and bioinformatics data structures, developing a stronger understanding of how genetic information can be translated into machine learning features. I learned how to balance model interpretability with predictive performance, particularly when comparing Logistic Regression and Random Forest approaches. Applying nested cross-validation taught me how to ensure reliable model selection and avoid data leakage, especially when working with imbalanced biological datasets. This project also deepened my understanding of antimicrobial resistance mechanisms and the role of antibiotic susceptibility testing (AST) data in research and clinical decision-making. Overall, it improved my proficiency in Python, pandas, and scikit-learn within an applied research context, strengthening both my technical and analytical skills.

---

## Dependencies

Install required packages:
```bash
pip install numpy pandas matplotlib scikit-learn scipy
