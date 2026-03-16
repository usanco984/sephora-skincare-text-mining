# sephora-skincare-text-mining
Text mining analysis of 40K+ Sephora skincare reviews using NLP and machine learning to uncover sentiment, customer themes, and recommendation patterns.


## Project Over
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
- whether some reviews may reflect promotional or influencer activity rather than organic feedback

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

## Analysis Tasks
This project included three main analyses:

### 1. Rating Classification
Reviews were classified into positive or negative classes based on product rating.

- Ratings 1–2 → Negative
- Ratings 4–5 → Positive
- Rating 3 was excluded as neutral

This task aimed to examine whether review text can predict explicit satisfaction levels.

### 2. Recommendation Classification
Reviews were classified based on whether the customer recommended the product.

This task aimed to examine whether review text can predict customer recommendation behavior, which may reflect a broader overall impression than rating alone.

### 3. Clustering and Sentiment Analysis
Unsupervised learning was applied to discover hidden themes in the review text, and sentiment analysis was used to evaluate the positive and negative tendencies expressed in reviews.

## Data Preparation
Different workflows were prepared for each task, but the general preparation process included:

- selecting relevant attributes
- removing missing values
- converting review text into text format
- balancing classes through sampling

For the two classification tasks, class imbalance was addressed by creating balanced datasets with equal numbers of positive and negative examples. This step was important because the original dataset contained many more positive reviews than negative ones. Without balancing, model performance could be biased toward the majority class.

Typical sample sizes used:

- Rating classification: 1,000–2,000 reviews per class
- Recommendation classification: 2,000 reviews per class
- Clustering: 1,000 reviews

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

## Key Results

### Rating Classification
The strongest models for rating classification were **Logistic Regression** and **SVM**.

Best result:
- **Logistic Regression with TF-IDF (80/20 split): 84.69% accuracy**

Main findings:
- Linear models performed best on this high-dimensional text classification task
- Decision Tree showed the weakest performance
- Naive Bayes provided a stable but lower-performing baseline
- TF and TF-IDF generally outperformed binary representations

An important finding was that the simplest preprocessing pipeline produced the best result. More complex preprocessing methods such as n-grams, token length filtering, and stemming did not consistently improve performance.

### Recommendation Classification
The strongest model for recommendation prediction was **Deep Learning**.

Best result:
- **Deep Learning: approximately 83% accuracy**

Main findings:
- Deep Learning performed slightly better than Logistic Regression and SVM
- For recommendation prediction, capturing broader context may be more important than in rating prediction
- In some cases, BTO and TO performed as well as or slightly better than TF-IDF
- Preprocessing changes had only small effects compared with model choice

### Clustering
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

### Sentiment Analysis
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
This project generated several business-relevant insights:

- customer reviews can be used to predict both satisfaction and recommendation behavior
- different business labels may require different modeling approaches
- recommendation intent and rating do not behave exactly the same way
- customer reviews reveal not only product feedback, but also signals of promotional campaign activity
- more preprocessing is not always better; simple pipelines may perform best

These findings could help retailers and brands better understand customer needs, improve products, and interpret online review quality more carefully.

---

## What Went Well
Several aspects of this project were successful:

- the workflow was organized clearly into data preparation, modeling, and evaluation
- multiple algorithms were compared systematically
- class imbalance was addressed through balanced sampling
- strong predictive performance was achieved, with the best models exceeding 82% accuracy
- clustering identified not only product themes but also a meaningful promotional review cluster

A particularly important takeaway was that the best-performing model depended on the target label. Logistic Regression and SVM performed strongly for rating classification, while Deep Learning performed best for recommendation prediction.

---

## Challenges
This project also involved several challenges:

- limited memory and computation capacity restricted some experiments
- some models required long processing times
- interpreting algorithm behavior required additional review and comparison
- some preprocessing methods were not explored as deeply as originally planned

These limitations affected how many experiments could be run and how extensively parameters could be tuned.

---

## Future Improvements
If this project were extended further, the following improvements would be valuable:

- compare results across additional text mining tools
- apply transformer-based NLP models such as BERT
- build custom dictionaries and domain-specific stopword lists
- analyze sentiment patterns within each cluster
- work with more raw and complex datasets
- connect text mining results more directly to practical business decisions

---

## Author
Yumi Kuwana  
M.S. in Data Analytics in Business  
Seattle Pacific University
