# Qure.ai — AI-Assisted TB Screening Prototype

## Introduction

This project demonstrates an educational machine learning pipeline for AI-assisted tuberculosis (TB) screening and prioritization.

The project is based on the business problem of supporting faster screening of chest X-rays while keeping clinicians responsible for final diagnosis and treatment decisions.

**Course:** Introduction to AI & ML
**Program:** BBA AI/ML
**Institution:** Chitkara Business School
**Organization:** Qure.ai

---

## Important Disclaimer

This notebook is an educational prototype only.

* It does not reproduce Qure.ai's proprietary qXR model.
* It does not use real chest X-ray images.
* It uses a synthetic tabular dataset for demonstration.
* It is not a clinical diagnostic system.
* Model performance should not be interpreted as clinical effectiveness.

---

## Business Problem

Large volumes of chest X-rays can create screening workload and delays, particularly in areas with limited specialist resources.

AI-assisted screening systems can help organize cases and prioritize those requiring clinical review.

The intended workflow is:

**Chest X-ray → AI Analysis → Screening/Priority Output → Clinician Review → Confirmatory Testing and Action**

AI is intended to support healthcare professionals rather than replace them.

---

## Project Objectives

* Understand the complete machine learning workflow.
* Demonstrate data collection and preprocessing.
* Build a binary classification model.
* Predict TB screening-positive cases.
* Evaluate model performance using standard classification metrics.
* Interpret model coefficients.
* Generate a screening-support priority flag.

---

## Dataset

Since no real patient or chest X-ray dataset was provided, this project creates a synthetic dataset of **300 screening cases**.

### Features

| Feature                | Description                                 |
| ---------------------- | ------------------------------------------- |
| Case_ID                | Unique screening case identifier            |
| Age                    | Age of the individual                       |
| Cough_Days             | Duration of cough                           |
| Weight_Loss            | Binary indicator for weight loss            |
| Fever                  | Binary indicator for fever                  |
| Prior_TB               | Previous TB history indicator               |
| Xray_Abnormality_Score | Synthetic abnormality score between 0 and 1 |
| Referral_Priority      | Synthetic referral priority indicator       |

### Target Variable

`TB_Screen_Positive`

* `1` = Synthetic screening-positive case
* `0` = Synthetic screening-negative case

The target variable is generated artificially for educational purposes.

---

## Machine Learning Pipeline

The notebook follows these 15 steps:

1. Data Collection
2. Data Understanding / Data Inspection
3. Data Cleaning
4. Outlier Detection & Treatment
5. Feature Selection
6. Define Target Variable
7. Encode Target Variable
8. Train-Test Split
9. Feature Standardisation
10. Model Building
11. Model Training
12. Prediction
13. Model Evaluation
14. Model Interpretation
15. Final Output

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook / Google Colab

---

## Machine Learning Model

The project uses **Logistic Regression** for binary classification.

Logistic Regression was selected because it is:

* Simple and fast.
* Suitable for binary classification.
* Relatively easy to interpret.
* Appropriate for demonstrating an introductory ML workflow.

A production chest X-ray screening system would generally require image-based deep learning methods, large clinical datasets, rigorous validation, and regulatory governance.

---

## Data Preprocessing

The following preprocessing techniques are applied:

### Missing Value Treatment

Missing numerical values are filled using the median.

### Invalid Value Handling

* Negative cough duration values are treated as invalid.
* Abnormality scores outside the range 0–1 are treated as invalid.

### Duplicate Removal

Duplicate rows are removed from the dataset.

### Outlier Treatment

The Interquartile Range (IQR) method is used to detect outliers, which are capped rather than removed.

### Feature Selection

The `Case_ID` column is removed because it is only an identifier.

---

## Model Training

The dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

A stratified train-test split is used to preserve target class proportions.

Features are standardized using `StandardScaler`, fitted only on the training data to avoid data leakage.

---

## Model Evaluation

The model is evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC
* Confusion Matrix

For screening-oriented applications, recall/sensitivity is an important metric to examine. However, no single metric is sufficient for clinical deployment.

---

## Final Output

The model generates:

* Actual screening labels.
* Predicted screening labels.
* Positive-class probabilities.
* Screening priority flags.

### Screening Flags

| Prediction | Output                       |
| ---------- | ---------------------------- |
| 1          | Priority for clinical review |
| 0          | Lower AI screening priority  |

These outputs are demonstrations of workflow prioritization only and are not medical recommendations.

---

## Business Interpretation

### How This Connects to Qure.ai

| Aspect             | Description                                                        |
| ------------------ | ------------------------------------------------------------------ |
| Business Problem   | Large volumes of chest X-rays can cause screening delays           |
| AI/ML Approach     | Computer vision and deep learning can analyze chest X-ray images   |
| Prototype Approach | Logistic Regression using synthetic tabular features               |
| Business Value     | Potentially faster screening and improved workflow organization    |
| Human Oversight    | Doctors and radiologists remain responsible for clinical decisions |

---

## Limitations

1. This project does not use real chest X-ray images.
2. The dataset is completely synthetic.
3. The target labels are artificially generated.
4. The model is not Qure.ai's proprietary qXR model.
5. Performance metrics cannot be used to claim clinical effectiveness.
6. Real-world deployment would require representative clinical data.
7. Privacy, security, external validation, monitoring, and regulatory governance would be essential.
8. This prototype should not be used for diagnosis or treatment decisions.

---

## How to Run the Project

### Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Run Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
QureAI_TB_Screening_ML_Pipeline (2).ipynb
```

Run all cells sequentially from top to bottom.

---

## Viva / Presentation Points

### Why Computer Vision?

Chest X-rays are image data, making computer vision suitable for extracting visual patterns.

### Why Machine Learning?

Machine learning can learn patterns from labelled examples and generate predictions or screening-support scores.

### Why Logistic Regression?

Logistic Regression is simple, fast, and relatively interpretable for demonstrating binary classification.

### What is the Target Variable?

`TB_Screen_Positive` is a synthetic binary classification label.

### What is the Business Output?

A screening-support prediction and priority flag that can help organize cases for clinical review.

### Does the AI Diagnose TB?

No. The AI supports screening and prioritization only. Clinicians remain responsible for final medical decisions.

---

## Project Structure

```text
QureAI-TB-Screening-ML-Pipeline/
│
├── QureAI_TB_Screening_ML_Pipeline.ipynb
├── README.md
└── requirements.txt
```

---

## Conclusion

This project demonstrates how a supervised machine learning pipeline can be applied to a healthcare screening workflow.

Although the implementation uses synthetic tabular data and Logistic Regression, it provides a foundation for understanding data preprocessing, model training, prediction, evaluation, and business interpretation in AI-assisted healthcare systems.

**AI should support clinical workflows, not replace professional medical judgment.**
