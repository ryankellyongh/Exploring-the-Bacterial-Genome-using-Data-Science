# Exploring the Bacterial Genome using Data Science

## Overview

This project applies machine learning to predict **cefepime antibiotic resistance** in *Escherichia coli* using genomic features. Two classification models — Logistic Regression and Random Forest — were trained and evaluated on gene presence/absence data and k-mer counts derived from bacterial genomes.

**Final model: Logistic Regression**, selected for its strong recall on resistant isolates and interpretable feature coefficients.

---

## Project Structure

train_test_data/
├── train_pa_genes.csv        # Training gene presence/absence matrix
├── test_pa_genes.csv         # Test gene presence/absence matrix
├── train_genes.csv           # Training gene alignment metadata
├── test_genes.csv            # Test gene alignment metadata
├── train_kmers.npy           # Training k-mer feature arrays
├── test_kmers.npy            # Test k-mer feature arrays
├── train_ids.npy             # Training genome IDs
├── test_ids.npy              # Test genome IDs
├── y_train.npy               # Resistance labels (R/S)
└── kmer_data_column_genes.npy

---

## Methods

### Data
- Features: Gene presence/absence matrices and k-mer count arrays
- Labels: Binary resistance classification — Resistant (R) or Susceptible (S) to cefepime

### Models
- Logistic Regression: default and tuned (liblinear, GridSearch over C and penalty)
- Random Forest: default and tuned (GridSearch over n_estimators, max_depth, min_samples)

### Evaluation
- Nested cross-validation (Outer: 5-fold, Inner: 3-fold GridSearchCV)
- Primary metric: Balanced Accuracy
- Secondary: Recall on resistant isolates, confusion matrix, classification report
- 20% stratified validation split for final model comparison

---

## Results

Logistic Regression was selected as the final model based on higher recall on resistant isolates, strong balanced accuracy, and interpretable feature importance via logistic coefficients.

---

## Requirements

numpy, pandas, matplotlib, scikit-learn, scipy

Install with:
pip install numpy pandas matplotlib scikit-learn scipy

---

## Usage

Open Exploring_the_Bacterial_Genome_using_Data_Science.ipynb in Jupyter. Update the data_dir path in load_data() to point to your local train_test_data/ folder:

load_data(data_dir='/path/to/your/train_test_data')

---

## Author

Ryan Kelly
