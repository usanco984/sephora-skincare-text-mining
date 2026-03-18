# Experiment 4: Sentiment Analysis

## Goal

The goal of this experiment was to analyze the overall sentiment of customer reviews and evaluate how preprocessing affects sentiment detection.

In addition to identifying positive and negative expressions in review text, this experiment also examines whether adding stemming changes sentiment scoring results.

---

## Experiment Setup

To examine whether preprocessing affects sentiment detection, two preprocessing configurations were compared.

Baseline preprocessing pipeline:

- Tokenize (mode: non letters)  
- Transform Case (lowercase conversion)  
- Stopwords filtering (English)  

Second configuration:

- Baseline preprocessing  
- + Stemming  

Both configurations generated approximately **2,500 attributes** for sentiment analysis.

The following metrics were evaluated:

- Sentiment score  
- Positivity  
- Negativity  

---

## Results

### Table 1: Sentiment Score Comparison

| Preprocessing | Average Sentiment Score |
|--------------|------------------------|
| Baseline preprocessing | 1.66 |
| Baseline + Stemming | 1.278 |

---

## Key Findings

Several important patterns were observed in the sentiment analysis results.

- Customer reviews in this dataset are **generally positive**, which is consistent with the rating distribution observed in previous experiments  
- Frequently observed **positive words** include:  
  - love, beauty, great, favorite, strong, pleasant  
- Common **negative words** include:  
  - hurt, dull, terrible, hate, disappointed  
- Reviews tend to show **higher positivity scores and relatively low negativity scores**  
- Adding stemming resulted in a **decrease in the average sentiment score**  

---

## Interpretation

The sentiment analysis results suggest that customers generally express **favorable opinions** about skincare products.

The prevalence of positive terms such as “love,” “great,” and “favorite” indicates strong customer satisfaction, while negative terms appear less frequently and are associated with specific dissatisfaction experiences.

The decrease in sentiment score after applying stemming suggests that preprocessing choices can influence how sentiment-related words are interpreted. Stemming reduces words to their root forms, which may alter how sentiment expressions are detected and scored by the sentiment analysis algorithm.

Overall, the sentiment patterns observed in this experiment are consistent with the results from the classification and clustering analyses. This alignment across multiple analytical approaches strengthens the conclusion that the dataset reflects predominantly positive customer sentiment.

These findings demonstrate that sentiment analysis can provide valuable insights into customer attitudes and complement other text mining techniques when analyzing large-scale review data.
