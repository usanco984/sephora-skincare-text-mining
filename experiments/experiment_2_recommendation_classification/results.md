# Experiment 2: Recommendation Classification

## Goal

The goal of this experiment was to predict whether a reviewer recommended a product based on the review text.

The classification target variable used in this experiment was:

- `is_recommended`

This task evaluates whether recommendation behavior can be inferred from textual information contained in customer reviews.

Because recommendation decisions may reflect overall impressions rather than only numerical evaluations, this experiment explores whether machine learning models can capture these patterns using text features.

---

## Experiment Setup

The original dataset contains more than 40,000 reviews, but the distribution of recommendation labels is highly imbalanced.

To ensure fair model training and evaluation, the dataset was reduced and balanced.

Final dataset configuration:

| Class | Value | Sample Size |
|------|------|------|
| Recommended | 1 | 2000 |
| Not Recommended | 0 | 2000 |

Total observations used: **4000 reviews**

To allow consistent comparison across models, the same preprocessing pipeline and experimental conditions were applied to all models.

---

## Model Comparison

To evaluate model performance for recommendation prediction, several classification algorithms were tested:

- Naive Bayes  
- Decision Tree  
- Logistic Regression  
- Support Vector Machine (SVM)  
- Deep Learning  
- k-Nearest Neighbors (k-NN, k = 5)  
- Random Forest  

Each model was evaluated using four document vector creation methods:

- Binary Term Occurrence (BTO)
- Term Occurrence (TO)
- Term Frequency (TF)
- TF-IDF

Two train–test splits were tested:

- **70% training / 30% testing**
- **80% training / 20% testing**

Due to memory limitations of the available hardware, **k-NN and Random Forest were only evaluated using TF-IDF in the 70/30 split experiments**.

---
## Table 1: Model Performance (70/30 Split)

| Model | BTO | TO | TF | TF-IDF |
|------|------|------|------|------|
| Naive Bayes | 68.00% | 67.25% | 68.42% | 67.00% |
| Decision Tree | 52.92% | 52.92% | 55.67% | 55.25% |
| Logistic Regression | 77.58% | 78.30% | 77.25% | 76.92% |
| SVM | 78.08% | 78.33% | 81.92% | 80.42% |
| Deep Learning | **82.83%** | 81.42% | 81.08% | 81.33% |
| k-NN (k=5) | — | — | — | 66.20% |
| Random Forest | — | — | — | 70.92% |

## Table 2: Model Performance (80/20 Split)

| Model | BTO | TO | TF | TF-IDF |
|------|------|------|------|------|
| Naive Bayes | 70.38% | 69.12% | 71.38% | 68.80% |
| Decision Tree | 53.50% | 53.50% | 56.25% | 54.87% |
| Logistic Regression | 77.50% | 79.00% | 78.50% | 77.12% |
| SVM | 78.38% | 78.00% | 83.12% | 81.00% |
| Deep Learning | **83.83%** | 83.25% | 82.62% | 82.50% |
| k-NN (k=5) | 71.00% | 74.00% | 74.00% | 74.00% |
| Random Forest | 64.25% | 63.38% | 71.62% | 72.25% |

## Preprocessing Improvement

Based on the previous model comparison results, **Deep Learning was selected as the best-performing model** for the recommendation classification task.

To explore whether additional preprocessing techniques could improve model performance, several preprocessing variations were tested while keeping the training/testing split fixed at **80/20**.

Although some feature weighting methods such as BTO, TO, and TF occasionally produced slightly higher accuracy, **TF-IDF was selected for preprocessing improvement experiments** to maintain consistency across experiments in this project.

Baseline preprocessing pipeline:

- Tokenize (non letters)
- Transform Case (lowercase conversion)
- Stopwords filtering (English)

Additional preprocessing techniques tested:

- Token length filtering
- N-gram generation
- Stemming (Porter, Snowball)

## Table 3: Preprocessing Impact (80/20 Split)

| Preprocessing Method | Accuracy (TF-IDF) |
|------|------|
| Baseline (Tokenize + Transform Case + Stopwords) | 82.50% |
| Baseline + Length(3–20) | 81.50% |
| Baseline + Length(3–20) + N-gram | 82.00% |
| Baseline + Length(3–20) + N-gram + Porter Stemming | 80.25% |
| Baseline + Length(3–20) + N-gram + Snowball Stemming | 80.38% |
| Baseline + Length(3–20) + N-gram + Porter Stemming | 81.75% |
| Baseline + N-gram + Porter Stemming | 81.00% |
| Baseline + Length(4–15) + N-gram + Porter Stemming | **83.00%** |
| Baseline + Length(4–15) + N-gram + Porter Stemming + Porter Stemming | 70.62% |

---

## Key Findings

Several important findings emerged from the recommendation classification experiments.

- **Deep Learning achieved the highest performance**, reaching approximately **83% accuracy** in the best configuration.
- **SVM and Logistic Regression also produced strong results**, but their performance was slightly lower than Deep Learning.
- **Decision Tree showed the weakest performance**, indicating that tree-based models struggled with high-dimensional text features.
- In several experiments, **BTO and TO representations produced slightly higher accuracy than TF-IDF**, suggesting that the presence of sentiment-related words may be more important than their frequency.

- The preprocessing experiments showed that techniques such as **token length filtering and n-gram generation produced only small improvements** in model performance.

---

## Interpretation

The results of the recommendation classification experiments showed slightly different patterns compared with the rating classification task. One possible explanation is that predicting whether a reviewer recommends a product requires capturing **more contextual meaning within the review text** than predicting rating values. Ratings are directly associated with numerical evaluations and may therefore be easier to predict using relatively simple linear models.

In contrast, recommendation decisions may depend on the overall impression expressed in the review, including tone, nuance, and the reviewer’s overall experience with the product. As a result, models such as Deep Learning, which can capture more complex patterns in textual data, may perform better for this task.

Interestingly, the results also showed that **BTO and TO representations sometimes performed as well as or slightly better than TF-IDF**. One possible explanation is that many reviews in the dataset are relatively short. In such cases, the presence of sentiment-related words may be more informative than their frequency.

Finally, the preprocessing experiments suggest that **model selection had a greater impact on performance than additional preprocessing techniques**. While some preprocessing variations slightly improved accuracy, the overall differences between configurations were relatively small.

Therefore, models capable of capturing deeper contextual patterns may perform better for this task.
