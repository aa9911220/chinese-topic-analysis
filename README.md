# Chinese Topic Analysis

A reproducible NLP pipeline for analyzing major issues and topics in Traditional Chinese news.

## Project Overview

This project investigates major issues and topics in Traditional Chinese news data, using multiple topic modeling approaches to identify, structure, and validate the issues being covered.

The project covers:

* Chinese text preprocessing
* Chinese word segmentation
* Keyword extraction
* Topic modeling (LDA and BERTopic)
* Issue classification
* Topic co-occurrence network analysis
* Cross-model consistency evaluation

## Research Questions

1. What are the major issues discussed in Traditional Chinese news?
2. Which issues frequently co-occur within the same articles?
3. How consistent are different topic modeling approaches (LDA vs. BERTopic) in identifying these issues?

## NLP Pipeline

```
Raw Data (News)
      ↓
Data Cleaning
      ↓
Chinese Tokenization
      ↓
Keyword Extraction
      ↓
Topic Modeling (LDA / BERTopic)
      ↓
Issue Classification
      ↓
Topic Co-occurrence Network
```

## Methods

| Method | Purpose | Status |
|---|---|---|
| Jieba | Chinese word segmentation | ✅ Done |
| TF-IDF | Keyword extraction | ✅ Done |
| TextRank | Keyword extraction | ✅ Done |
| LDA | Topic modeling | ✅ Done (K=10 selected via coherence score) |
| NetworkX | Topic co-occurrence network | ✅ Done (LDA-based) |
| BERTopic | Topic modeling | 🔄 In progress |
| Logistic Regression | Issue classification | ⏳ Planned |
| BERT | Issue classification | ⏳ Planned |

## Current Results

* **LDA (K=10)** was selected as the best-performing topic count based on `c_v` coherence scores.
* A **topic co-occurrence network** was built from the LDA document-topic distributions (PMI-weighted edges, threshold-filtered), revealing three interpretable issue clusters:
  * **Political / social events** (e.g. political parties, government affairs, police/incident reports)
  * **International / economic affairs** (e.g. cross-strait relations, markets, investment, education/history)
  * **Lifestyle / leisure** (e.g. food, health, daily life)
* Cluster structure was cross-validated against the original news site tag labels, with the political cluster showing the strongest agreement.

## Next Steps

* Complete BERTopic modeling on the same news corpus.
* Compare LDA and BERTopic outputs at the document level using **Adjusted Rand Index (ARI)** and **Normalized Mutual Information (NMI)** to quantify cross-model consistency (RQ3).
* Optionally, build a BERTopic-based co-occurrence network to visually compare community structure against the LDA network.

## Reproducibility

The preprocessing and analysis pipeline is implemented in Python. Data sources and processing steps will be documented to facilitate reproducibility.
