# Experiment 2: Recommendation Classification

## Goal

The goal of this experiment is to determine whether review text can predict whether a customer recommends a product.

The target variable used for classification was:

- `is_recommended`

This experiment examines whether recommendation behavior can be inferred from textual feedback alone.

---

## Data Preparation

The dataset originally contained a large imbalance between recommended and non-recommended reviews.  
To address this issue, the dataset was balanced using sampling.

Final dataset used:

| Class | Sample Size |
|------|------|
| Recommended | 2000 |
| Not Recommended | 2000 |

Total observations used: **4000 reviews**

---

## Text Preprocessing

Baseline preprocessing steps:

- Tokenize (non letters)
- Transform Case (lowercase)
- Stopwords filtering

Additional experiments included:

- Token length filtering
- n-grams
- stemming

---

## Model Comparison

| Model | BTO | TO | TF | TF-IDF |
|------|------|------|------|------|
| Naive Bayes | 70.38% | 69.12% | 71.38% | 68.80% |
| Decision Tree | 53.50% | 53.50% | 56.25% | 54.87% |
| Logistic Regression | 77.50% | 79.00% | 78.50% | 77.12% |
| SVM | 78.38% | 78.00% | 83.12% | 81.00% |
| Deep Learning | **83.83%** | 83.25% | 82.62% | 82.50% |

---

## Key Findings

The strongest performing model was **Deep Learning**, achieving approximately **83% accuracy**.

Important observations:

- Deep learning slightly outperformed traditional models
- Recommendation prediction appears to require capturing broader contextual meaning in reviews
- Linear models such as Logistic Regression and SVM also performed well

---

## Interpretation

Unlike rating prediction, recommendation behavior may reflect broader product impressions, including:

- value perception
- expectations
- brand perception

Therefore, models capable of capturing deeper contextual patterns may perform better for this task.
