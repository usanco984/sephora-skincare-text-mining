# sephora-skincare-text-mining
Text mining analysis of 40K+ Sephora skincare reviews using NLP and machine learning to uncover sentiment, customer themes, and recommendation patterns.

## Project Overview
This project analyzes more than 40,000 Sephora skincare product reviews using text mining and machine learning techniques to extract customer insights from large-scale review data.The objective was to identify what customers like or dislike based on review text, product ratings, and recommendation behavior.

Because online retailers receive thousands of customer reviews, it is difficult to manually interpret all feedback. This project demonstrates how text mining can transform large-scale unstructured review data into actionable business insights related to customer satisfaction, product performance, and marketing impact.

In addition to classification, this project also compares different prediction targets and explores hidden themes in customer feedback through clustering and sentiment analysis.

---

## Business Problem
Customer reviews contain valuable information that can help companies improve product quality, customer satisfaction, and marketing strategy. However, online retailers often receive thousands of reviews, making it difficult to manually analyze all customer feedback.

Text mining provides a scalable way to extract insights from large volumes of review data. By analyzing review text, businesses can better understand:

- the factors driving customer satisfaction and dissatisfaction
- which product features customers discuss most frequently
- whether customers are likely to recommend a product
- whether Some reviews may originate from promotional or influencer sampling programs
  
To explore these questions, this project focuses on two related prediction tasks:

1. **Rating classification** – predicting whether a review reflects positive or negative sentiment based on the product rating.
2. **Recommendation classification** – predicting whether a customer recommends the product based on the review text.

In addition, unsupervised learning techniques were used to identify hidden themes and patterns in customer reviews through clustering and sentiment analysis. 
The analysis therefore combines supervised learning for prediction tasks and unsupervised learning for theme discovery.

---

## Dataset
The dataset used in this project was obtained from Kaggle and contains more than 40,000 customer reviews of Sephora skincare products.

Main attributes used in this study:

- `review_text`: customer-written review text
- `rating`: product rating from 1 to 5
- `is_recommended`: whether the reviewer recommends the product

Dataset source:  
[Sephora Skincare Reviews on Kaggle](https://www.kaggle.com/datasets/melissamonfared/sephora-skincare-reviews)

## Why RapidMiner Was Selected
RapidMiner was selected as the primary tool because it provides a visual workflow environment and built-in text mining operators. This made it possible to perform preprocessing, feature extraction, classification, clustering, and sentiment analysis efficiently without extensive programming.

The platform was especially useful for comparing multiple algorithms and preprocessing variations within one consistent environment.

---

This project consists of four main analyses combining supervised and unsupervised learning to extract insights from customer reviews.

---

### 1. Rating Classification
Predicting whether a review is positive or negative based on rating.

- Best Model: Logistic Regression  
- Best Accuracy: **84.69% (TF-IDF, 80/20 split)**  
- Insight: Linear models performed best for rating prediction  

👉 [View Details](experiments/experiment_1_rating/results.md)

---

### 2. Recommendation Classification
Predicting whether a customer recommends a product based on review text.

- Best Model: Deep Learning  
- Best Accuracy: **~83%**  
- Insight: Recommendation prediction requires capturing broader context  

👉 [View Details](experiments/experiment_2_recommendation/results.md)

---

### 3. Clustering Analysis
Identifying hidden themes in customer reviews using unsupervised learning.

- Key Topics: acne, dry skin, cleansing, moisturizer, face mask  
- Insight: Customer concerns and product usage patterns were clearly identified  
- Additional Finding: Detected a **promotional / influencer review cluster**  

👉 [View Details](experiments/experiment_3_clustering/results.md)

---

### 4. Sentiment Analysis
Analyzing overall sentiment and the impact of preprocessing.

- Overall Sentiment: **Positive**  
- Key Finding: Stemming reduced sentiment scores  
- Insight: Preprocessing choices can affect sentiment detection  

👉 [View Details](experiments/experiment_4_sentiment/results.md)

---

# Analysis Tasks

This project includes four analytical experiments:

### 1 Rating Classification
Classifying reviews as **positive or negative sentiment based on product rating**.

Ratings were converted into binary classes:

- 1–2 → Negative  
- 4–5 → Positive  
- Rating 3 was excluded as neutral

---

### 2 Recommendation Classification
Predicting **whether a customer recommends the product** based on review text.

This task examines whether recommendation behavior can be predicted using textual feedback.

---

### 3 Clustering Analysis
Unsupervised learning was used to **identify hidden themes and discussion topics in customer reviews**.

K-means clustering was applied after dimensionality reduction.

---

### 4 Sentiment Analysis
Sentiment analysis was applied to measure the **overall positive and negative tone expressed in customer reviews**.

## Data Preparation
Different workflows were prepared for each task, but the general preparation process included:

- selecting relevant attributes
- removing missing values
- converting review text into text format
- balancing classes through sampling

For the two classification tasks, class imbalance was addressed by creating balanced datasets with equal numbers of positive and negative examples. This step was important because the original dataset contained many more positive reviews than negative ones. Without balancing, model performance could be biased toward the majority class.

Typical sample sizes used:

| Task | Sample Size |
|-----|-----|
| Rating Classification | 4,000 reviews |
| Recommendation Classification | 4,000 reviews |
| Clustering | 1,000 reviews |
---

## Text Preprocessing
Text preprocessing was performed using **Process Documents from Data** in RapidMiner.

Baseline preprocessing steps:

- Tokenize (non letters)
- Transform Cases (lowercase)
- Filter Stopwords (English)

Additional preprocessing experiments included:

- Filter Tokens by Length
- Generate n-Grams
- Stemming (Porter, Snowball)

These variations were tested to evaluate their effect on model performance.

---

## Algorithms Used
To compare different modeling approaches for high-dimensional text data, the following algorithms were tested:

- Naive Bayes
- Decision Tree (Gain Ratio)
- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest
- k-Nearest Neighbors (kNN)
- Deep Learning

For unsupervised analysis, the following were used:

- Singular Value Decomposition (SVD)
- K-means Clustering
- Extract Sentiment
- Aggregate

---

## Experimental Design
For both classification tasks, models were compared using four document vector weighting methods:

- Binary Term Occurrence (BTO)
- Term Occurrence (TO)
- Term Frequency (TF)
- TF-IDF

Two train-test splits were evaluated:

- 70% / 30%
- 80% / 20%

This allowed systematic comparison across models and feature representations.

---
## Experiments

This project includes four analytical experiments.  
Detailed results and analysis for each experiment can be found below.

- [Experiment 1 – Rating Classification](experiments/experiment_1_rating_classification/results.md)

- [Experiment 2 – Recommendation Classification](experiments/experiment_2_recommendation_classification/results.md)

- [Experiment 3 – Clustering Analysis](experiments/experiment_3_clustering/results.md)

- [Experiment 4 – Sentiment Analysis](experiments/experiment_4_sentiment_analysis/results.md)

---

## Key Results

### Experiment 1 - Rating Classification
The strongest models for rating classification were **Logistic Regression** and **SVM**.

Best result:
- **Logistic Regression with TF-IDF (80/20 split): 84.69% accuracy**

Main findings:
- Linear models performed best on this high-dimensional text classification task
- Decision Tree showed the weakest performance
- Naive Bayes provided a stable but lower-performing baseline
- TF and TF-IDF generally outperformed binary representations

An important finding was that the simplest preprocessing pipeline produced the best result. More complex preprocessing methods such as n-grams, token length filtering, and stemming did not consistently improve performance.

### Experiment 2 - Recommendation Classification
The strongest model for recommendation prediction was **Deep Learning**.

Best result:
- **Deep Learning: approximately 83% accuracy**

Main findings:
- Deep Learning performed slightly better than Logistic Regression and SVM
- For recommendation prediction, capturing broader context may be more important than in rating prediction
- In some cases, BTO and TO performed as well as or slightly better than TF-IDF
- Preprocessing changes had only small effects compared with model choice

### Experiment 3 - Clustering
Clustering revealed several meaningful customer review themes, including:

- acne / dry skin concerns
- moisturizing and eye cream products
- face masks and pore treatment
- cleansing and makeup removal
- promotional / influencer reviews

One particularly interesting cluster contained words such as:

- received
- influenster
- complimentary
- free

This suggests that some reviews may have been influenced by promotional or influencer campaigns rather than reflecting purely organic customer experiences.

### Experiment 4 - Sentiment Analysis
Sentiment analysis showed that the overall review dataset was generally positive, which was consistent with the rating distribution.

Examples of frequently observed positive terms:
- love
- great
- favorite
- beauty

Examples of negative terms:
- hate
- terrible
- disappointed
- hurt

The average sentiment score decreased after stemming was added, suggesting that preprocessing choices can influence sentiment detection results.

---

## Business Insights
The results of this analysis provide several insights that may be useful for businesses analyzing large-scale customer review data. 

First, the results demonstrate that customer review text can serve as a valuable source of information for predicting customer satisfaction and recommendation behavior. Even when only the written review text was used as input, machine learning models were able to predict rating sentiment and recommendation outcomes with relatively strong accuracy. This suggests that companies can use text mining techniques to monitor customer feedback at scale and detect potential satisfaction issues earlier than through manual review. 

Second, the results indicate that product ratings and recommendation behavior represent related but distinct aspects of customer evaluation. Product ratings tend to reflect direct product satisfaction, such as product performance or usability. In contrast, recommendation behavior may reflect a broader overall impression of the product, including factors such as value, expectations, and brand perception. In this study, Logistic Regression and SVM performed best for rating prediction, while Deep Learning showed slightly stronger performance for recommendation prediction. This difference suggests that predicting recommendation behavior may require capturing more complex contextual information from review text. 

Third, the clustering analysis revealed several meaningful themes in customer reviews. These included discussions related to skincare concerns such as acne and dry skin, product types such as moisturizers or face masks, and usage experiences such as cleansing and makeup removal. These patterns suggest that customer reviews frequently focus on product performance and skincare problems, which can help companies better understand the needs and expectations of their customers. An additional interesting finding was the presence of a cluster associated with promotional or influencer-related reviews. Words such as “received,” “complimentary,” “influencer,” and “free” frequently appeared together in one cluster. This suggests that some reviews may originate from promotional sampling programs rather than purely organic customer experiences. For companies analyzing review data, recognizing the presence of promotional reviews may be important when interpreting overall customer sentiment. 

Overall, the findings suggest that text mining of customer reviews can support business decision making by helping companies better understand customer opinions, detect common product concerns, and identify patterns in customer feedback that may not be immediately visible through manual analysis.
---

## What Went Well
Several aspects of this project were successful:

- The workflow was organized clearly into data preparation, modeling, and evaluation
- <Multiple algorithms were compared systematically
- Class imbalance was addressed through balanced sampling
- Strong predictive performance was achieved, with the best models exceeding 82% accuracy
- Clustering identified not only product themes but also a meaningful promotional review cluster

A particularly important takeaway was that the best-performing model depended on the target label. Logistic Regression and SVM performed strongly for rating classification, while Deep Learning performed best for recommendation prediction.

---

## Challenges
This project also involved several challenges:

- Limited memory and computation capacity restricted some experiments
- Some models required long processing times
- Interpreting algorithm behavior required additional review and comparison
- Some preprocessing methods were not explored as deeply as originally planned

These limitations affected how many experiments could be run and how extensively parameters could be tuned.

---

## Future Improvements
If this project were extended further, the following improvements would be valuable:

- Compare results across additional text mining tools
- Apply transformer-based NLP models such as BERT
- Build custom dictionaries and domain-specific stopword lists
- Analyze sentiment patterns within each cluster
- Work with more raw and complex datasets
- Connect text mining results more directly to practical business decisions

---

## Author
Yumi Kuwana  
M.S. in Data Analytics in Business  
Seattle Pacific University
