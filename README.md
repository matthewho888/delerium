# COVID Delirium Prediction

Machine learning models to predict whether COVID-19 patients will develop **delirium** during hospitalization, using structured **demographic** data and **admission transcriptomic features**.

This project includes:
- Logistic regression with clinical features
- PCA + gene expression modeling
- Exploratory steps for combining both and building interpretable models

---

## Data Sources

- `delirium cohort demographics.xlsx` — Patient demographics and clinical metrics
- `admission_annotation.csv` — Metadata for patient samples
- `admission_norm_gene_exp_df.csv` — Normalized gene expression values (admission)
- `serial_samples_annotation.csv`, `serial_norm_gene_exp_df.csv` — For longitudinal model (planned)
- `Gene_symbols.csv` — Gene ID metadata

---

## Tools & Libraries

`Python`, `pandas`, `scikit-learn`, `seaborn`, `matplotlib`, `shap`, `SMOTE`, `PCA`  
Models: `LogisticRegression`, `RandomForestClassifier`, `GradientBoostingClassifier`

---

## What’s Implemented

### Model 1: Demographic-Only Prediction

- Cleaned structured fields: Age, Sex, Race, Dementia, WHO Scale, SOFA
- Preprocessed using `StandardScaler` and `OneHotEncoder`
- Trained a **Logistic Regression** model
- Evaluated with: Accuracy, Precision, Recall, AUC-ROC
- Visualized using ROC curve

### Model 2: Transcriptomic-Only Prediction

- Merged admission annotation and gene expression by ID
- Transposed gene expression matrix
- Applied PCA (10 components) to reduce high-dimensional gene space
- Trained:
  - Logistic Regression
  - Random Forest (with `class_weight='balanced'`)
- Evaluated similarly using metrics and ROC curves

---

## Example Performance (Logistic Regression)

| Model | Accuracy | Precision | Recall | AUC-ROC |
|-------|----------|-----------|--------|---------|
| Clinical Only | ~0.87 | ~0.40 | ~0.67 | ~0.90 |
| Transcriptomics (PCA) | varies | varies | varies | ~0.88–0.91 |

> Results vary slightly with train/test split — class imbalance was handled with `SMOTE` and model weighting.

---

## Next Steps

- Combine PCA gene components with clinical features (Model 3)
- Build longitudinal gene model using serial data (Model 4)
- Use SHAP to explain key features
- Reduce gene set for clinical testing feasibility

---

## Files

| File | Description |
|------|-------------|
| `delirium_prediction_model.ipynb` | Main notebook with Models 1 and 2 |
| `data/` | Local dataset directory (not uploaded to GitHub) |
| `images/` | ROC, SHAP, and PCA visualizations (optional) |
| `README.md` | This file

---

## 🧠 Background

Delirium is a fluctuating disturbance in attention and cognition often seen in COVID-19 patients, with multifactorial causes including inflammation. Early prediction is critical but difficult, as pharmacological interventions are limited and detection is often delayed.

---

## 📫 Contact

- Email: [26matthewho@berkeley.edu](mailto:26matthewho@berkeley.edu)
- GitHub: [matthewho](https://github.com/matthewho)

---

> Note: No sensitive patient data is included in this repository.
