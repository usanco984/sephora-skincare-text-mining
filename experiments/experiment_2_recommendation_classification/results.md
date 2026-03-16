# Experiment 2: Recommendation Classification

## Goal

The goal of this experiment was to predict whether a reviewer recommended a product based on the review text.

The classification target variable used in this experiment was:

- `is_recommended`

This task evaluates whether recommendation behavior can be inferred from textual information contained in customer reviews.

Because recommendation decisions may reflect overall impressions rather than only numerical evaluations, this experiment explores whether machine learning models can capture these patterns using text features.

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
