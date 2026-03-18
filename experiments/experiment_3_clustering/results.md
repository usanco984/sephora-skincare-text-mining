# Experiment 3: Clustering Analysis

## Goal

The goal of this experiment was to identify hidden themes in customer reviews using unsupervised learning techniques.

Unlike classification tasks, clustering does not rely on predefined labels. Instead, it groups reviews based on textual similarity, allowing discovery of underlying patterns and topics within the dataset.

---

## Experiment Setup

To explore underlying themes within the review dataset, an unsupervised learning approach was applied using:

- Singular Value Decomposition (SVD) for dimensionality reduction  
- K-means clustering for grouping similar reviews  

For computational efficiency, the dataset was reduced to **1,000 reviews**.

The same preprocessing pipeline used in previous experiments was applied:

- Tokenize (mode: non letters)  
- Transform Case (lowercase conversion)  
- Stopwords filtering (English)  

After preprocessing, SVD was applied to reduce the dimensionality of the document-term matrix, and K-means clustering was used to group reviews with similar textual patterns.

Two clustering configurations were tested:

- **k = 4 clusters**
- **k = 5 clusters**

---

## Clustering Results

### Table 1: Cluster Interpretation (k = 4)

| Cluster | Size | Top Words | Topic Interpretation |
|--------|------|-----------|----------------------|
| 0 | 125 | cleanser, makeup, clean, feeling, face | Cleansing / makeup removal |
| 1 | 430 | acne, product, use, dry | Skin problems / acne / dry skin |
| 2 | 331 | mask, cream, smooth, amazing | Product performance / moisturizing |
| 3 | 114 | received, influenster, complimentary | Promotional reviews |

---

### Table 2: Cluster Interpretation (k = 5)

| Cluster | Size | Top Words | Topic Interpretation |
|--------|------|-----------|----------------------|
| 0 | 375 | acne, dry, face, product | Skin problems / acne & dry skin |
| 1 | 122 | cream, eye, gel, lightweight, moisturizer | Moisturizing / eye cream |
| 2 | 180 | mask, pores, smooth, recommend | Face mask / pore treatment |
| 3 | 188 | cleanser, clean, makeup, gentle | Cleansing / makeup removal |
| 4 | 135 | received, influenster, free, complimentary | Promotional / influencer reviews |

---

## Key Findings

Several meaningful patterns emerged from the clustering analysis.

- Customer reviews frequently focused on **specific skincare concerns**, such as acne and dry skin  
- Distinct clusters captured **product usage categories**, including moisturizers, face masks, and cleansers  
- Increasing the number of clusters from 4 to 5 resulted in **more detailed and interpretable topic separation**  
- A distinct cluster containing words such as *“received,” “influenster,” “free,” and “complimentary”* was identified  

---

## Interpretation

The clustering results suggest that customer reviews are strongly centered around **product performance and skincare concerns**.

Topics such as acne treatment, moisturizing products, face masks, and cleansing routines reflect the primary interests and needs of customers. These patterns indicate that reviews can provide valuable insights into customer expectations and product usage behavior.

An especially important finding is the presence of a **promotional or influencer-related cluster**. Reviews in this cluster likely originate from promotional campaigns or product sampling programs rather than purely organic customer experiences.

This distinction is important for businesses because promotional reviews may influence overall sentiment and customer perception. Recognizing these patterns can help companies better interpret review data and make more informed decisions based on customer feedback.
