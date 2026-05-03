---
title: Assignment 4 - Text Analytics using Quanteda
layout: default
---

# Assignment 4: Text Analytics using Quanteda

## 1. Introduction
This assignment applies the **quanteda** package in R to perform text analytics on US presidential inaugural speeches and Department of Defense (DOD) reports. The workflow includes corpus creation, tokenization, document-feature matrices (DFM), and **Wordfish scaling**.

---

## 2. Analysis of US Presidential Inaugural Speeches

### 2.1 Data and Method
- Dataset: `data_corpus_inaugural` (2000–2025)
- Preprocessing:
  - Remove punctuation, numbers, symbols, URLs
  - Convert to lowercase
  - Remove stopwords and common functional words

- DFM trimming:
  - Minimum: 2 documents
  - Maximum: 80% of documents

---

### 2.2 Top Words

| Rank | Word       | Frequency |
|------|------------|----------|
| 1    | freedom    | 42       |
| 2    | liberty    | 25       |
| 3    | let        | 20       |
| 4    | story      | 18       |
| 5    | democracy  | 16       |

👉 These reflect **democratic values and national identity**.

---

### 2.3 Similarities and Differences

**Similarities:**
- National unity  
- Democratic values  
- Peaceful transfer of power  

**Differences:**
- Trump → negative theta (distinct rhetoric)  
- Obama → internationalist themes  
- Bush → strong positive clustering  

---

## 3. What is Wordfish?

Wordfish is an **unsupervised text scaling method** that:

- Uses word frequencies  
- Estimates document positions (**theta**)  
- Identifies latent dimensions  

### Key Parameters:
- θ (theta): document position  
- β (beta): word discrimination  
- ψ (psi): word frequency baseline  

---

## 4. Wordfish Results – Inaugural Speeches

| President | Year | Theta |
|----------|------|------|
| Trump    | 2017 | -1.323 |
| Trump    | 2025 | -1.307 |
| Biden    | 2021 | -0.080 |
| Obama    | 2009 | 0.053 |
| Obama    | 2013 | 0.540 |
| Bush     | 2001 | 1.044 |
| Bush     | 2005 | 1.073 |

---

## 5. Interpretation

### Key Findings

- **Most positive:** Bush 2005 → traditional rhetoric  
- **Most negative:** Trump 2017 → populist rhetoric  
- **Trend:** Speeches becoming more traditional over time  

---

## 6. Analysis of DOD Reports

### 6.1 Data
12 reports (2001–2023)

### 6.2 Top Words

| Rank | Word        |
|------|------------|
| 1    | operations |
| 2    | defense    |
| 3    | capabilities |

👉 Focus: **strategy + operations**

---

## 7. Wordfish Results – DOD

| Year | Secretary | Theta |
|------|----------|------|
| 2001 | Rumsfeld | -0.888 |
| 2017 | Mattis   | 1.320 |
| 2023 | Austin   | 1.520 |

---

### Key Insights

- Most hawkish: Austin 2023  
- Most cautious: Esper 2019  
- Trend: Increasingly hawkish  

---

## 8. Comparative Analysis

| Dimension | Inaugural Speeches | DOD Reports |
|----------|------------------|------------|
| Focus    | Values           | Strategy   |
| Tone     | Inspirational    | Technical  |
| Vocabulary | Abstract      | Concrete   |

👉 No shared vocabulary → **completely different domains**

---

## 9. Conclusion

### Main Takeaways

1. Inaugural speeches:
   - Consistent themes (freedom, democracy)
   - Variation in rhetorical style  

2. DOD reports:
   - Operational and strategic focus  
   - Increasingly hawkish  

3. Wordfish:
   - Captures latent dimensions  
   - No labeled data required  

---

## 10. Appendix (Code)

```r
library(quanteda)
library(quanteda.textmodels)

data("data_corpus_inaugural")

corpus <- corpus_subset(data_corpus_inaugural, Year >= 2000)

tokens <- tokens(corpus, remove_punct = TRUE) %>%
  tokens_tolower() %>%
  tokens_remove(stopwords("en"))

dfm_mat <- dfm(tokens)

model <- textmodel_wordfish(dfm_mat)

summary(model)
