# Experiment 1: Rating Classification

## Goal

The goal of this experiment is to determine whether review text can predict customer sentiment based on product ratings.

The rating variable was converted into binary classes:

- Ratings **1–2 → Negative**
- Ratings **4–5 → Positive**
- Rating **3 was excluded** as neutral

This experiment evaluates whether machine learning models can predict review sentiment using only textual information.

---

## Data Preparation

The original dataset contains a large imbalance between positive and negative reviews.

To avoid biased model performance, the dataset was balanced through sampling.

Final dataset used:

| Class | Sample Size |
|------|------|
| Positive | 2000 |
| Negative | 2000 |

Total observations used: **4000 reviews**

---

## Text Preprocessing

Baseline preprocessing steps:

- Tokenize (non letters)
- Transform Case (lowercase)
- Stopwords filtering (English)

Additional preprocessing experiments included:

- Token length filtering
- n-gram generation
- stemming (Porter and Snowball)

---

# Model Comparison

Two train–test splits were evaluated:

- **70 / 30**
- **80 / 20**

Four document vector weighting methods were tested:

- Binary Term Occurrence (BTO)
- Term Occurrence (TO)
- Term Frequency (TF)
- TF-IDF

---

## Table 1: Model Performance (70/30 Split)

| Model | BTO | TO | TF | TF-IDF |
|------|------|------|------|------|
| Naive Bayes | 68.88% | 68.33% | 72.92% | 72.04% |
| Decision Tree | 60.71% | 60.71% | 59.62% | 59.00% |
| Logistic Regression | 83.42% | 81.38% | 83.20% | 82.67% |
| SVM | 80.80% | 80.58% | **83.92%** | 83.25% |

---

## Table 2: Model Performance (80/20 Split)

| Model | BTO | TO | TF | TF-IDF |
|------|------|------|------|------|
| Naive Bayes | 69.88% | 68.75% | 73.38% | 72.62% |
| Decision Tree | 60.38% | 60.38% | 59.25% | 60.25% |
| Logistic Regression | **84.56%** | 84.31% | 80.50% | **84.69%** |
| SVM | 82.00% | 81.50% | 83.88% | 83.62% |

---

## Table 3: Extended Model Comparison (80/20 Split)

Additional algorithms were evaluated to further explore model performance.

| Model | BTO | TO | TF | TF-IDF |
|------|------|------|------|------|
| Naive Bayes | 69.67% | 68.50% | 71.00% | 70.50% |
| Logistic Regression | 78.50% | 79.00% | 79.00% | 79.67% |
| Random Forest | 67.33% | 66.83% | 74.33% | 72.17% |
| k-NN (k=5) | 64.17% | 63.17% | 70.00% | 76.50% |
| Deep Learning | **82.33%** | 80.50% | 80.50% | 80.33% |

---

## Table 4: Preprocessing Impact (80/20 Split)

| Preprocessing Method | Accuracy (TF-IDF) |
|------|------|
| Baseline (Tokenize + Transform Case + Stopwords) | **84.69%** |
| Baseline + Length (3–20) | 77.81% |
| Baseline + Length (3–20) + N-gram | 72.94% |
| Baseline + Length (3–20) + N-gram + Porter Stemming | 77.19% |
| Baseline + Length (3–20) + N-gram + Snowball Stemming | 76.25% |
| Baseline + Length (4–15) + N-gram + Porter Stemming | 74.83% |

---

# Key Findings

Several important findings emerged from this experiment.

First, **Logistic Regression and SVM achieved the strongest performance** among the tested models.  
The best result was achieved by **Logistic Regression with TF-IDF using an 80/20 split**, reaching **84.69% accuracy**.

Second, traditional linear models performed particularly well for high-dimensional text data.  
Tree-based models such as Decision Tree performed significantly worse.

Third, the results show that **more complex preprocessing did not necessarily improve performance**.  
The simplest preprocessing pipeline produced the highest accuracy.

---

# Interpretation

These findings suggest that:

- Linear models are highly effective for text classification tasks.
- Increasing preprocessing complexity may introduce noise rather than improving model performance.
- TF-IDF remains one of the most reliable representations for text classification problems.

Overall, this experiment demonstrates that customer sentiment expressed in review text can be predicted with relatively high accuracy using machine learning techniques.
