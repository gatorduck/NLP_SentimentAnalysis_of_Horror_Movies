# NLP Sentiment Analysis of Horror Movies

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-154F3C?style=flat&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)

> **TL;DR:** Sentiment analysis and K-means clustering of 80 horror movie reviews using NLTK, SentiWordNet, and TF-IDF. Cluster 1 movies (fun, zombies) score highest; Cluster 5 ("boring") scores lowest.

## Overview

Topics covered here are foundations for large language models (LLMs) or the popular ChatGPT. We focus on a sub branch of natural language processing (NLP), natural language understanding. 

```mermaid
flowchart TB
    NLP --> NLU & NLG
```

This can even be dissected further as there are different layers to NLP that can be built on each other: lexical, syntactic, semantic, discourse layers. This analysis will primarily be a shallow approach. 

There are many horror movies, many which are unfortunately horrible. I use my NLP expertise for my analysis. Oh and if I didn't mention it already horror movies are my favorite movie genre. We will also use this same text to cluster movies by similarity. 

## General Prep

General data prep for NLP utilized in this repo includes:

 1. Tokenization per word / unigrams
 2. Removing stop words
 3. Identifying parts of speech for each of these tokens such as adjective, noun, etc.

- _maxent_treebank_pos_tagger_ - Penn Treebank Tagset, which uses Penn Treebank corpus training on Wall Street Journal data

## Sentiment Analysis

Using our tokenized words and part of speech sets we tally negative and positive scores. We use scores associated with our words found in the SentiWordNet lexicon used for opinion mining. We supplement our tokens with synonyms for each of our tokens as their corresponding scores.

Adding score and overall verbal sentiment, e.g. positive or negative. We see that the Ghost Ship movie had a positive review, in this case anything with sentiment scores greater than or equal to zero are labelled as positive. This may not accurately represent how great the movie is, as this is only 1 review per movie. We could scrape over hundreds of reviews per movie to make this even greater.

![Sentiment scores](image/scores.png)

## Clustering

For the last section we use term frequency and apply weights to emphasize words unique to our movie reviews using TF-IDF. For clustering we use K-means clustering to identify movies based on our features.

On average cluster 1 had higher positive sentiment scores. Common features that help contribute to this score are these movies are described as fun and have zombies. Cluster 5 on average had the lowest scores, with common features that include negative sentiment through words such as 'boring'. Overall there is positive sentiment for horror movies, but not exactly great films. Up next, let's find out what exactly is boring about these movies by using ngrams and chunkers.

![Clusters 1 and 5](image/clusters.png)

## Project Structure

```
├── README.md
├── .gitignore
├── requirements.txt
├── data/                   # Raw and processed data (CSV, pickle, JSON)
├── image/                  # Visualizations
└── notebooks/              # Jupyter notebooks
    ├── 01_collecting_data.ipynb
    ├── 02_preprocessing_txt.ipynb
    ├── 03_sentiment_analysis.ipynb
    └── 04_clustering.ipynb
```

## Setup

```sh
python -m venv venv
venv\Scripts\activate    # Windows
pip install -r requirements.txt
```
