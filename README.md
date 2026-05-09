# Social Media Analytics — Travel Destination Sentiment & Network Analysis

## Overview

This project analyses travel-related discussions scraped from **Reddit** and **YouTube** to investigate sentiment trends, the impact of global events on travel interest, and co-mention network structures across countries.

Three hypotheses are tested:

| # | Hypothesis |
|---|------------|
| 1 | Reddit and YouTube exhibit significantly different sentiment trends for the same countries over the same period |
| 2 | Global events affect which travel destinations are discussed |
| 3 | Co-mentioned country networks form culturally/regionally coherent communities (Louvain detection) |

---

## Repository Structure

```
.
├── Data Collection/
│   ├── Reddit_data_collection_by_subreddits.ipynb   # Reddit collection via PRAW
│   ├── reddit_data_collect_usong_search query.ipynb  # Reddit search-query collection
│   └── YouTube_data_collection.ipynb                # YouTube Data API collection
│
├── Main Analysis/
│   ├── EDA.ipynb       # Exploratory data analysis
│   ├── Hypo1.ipynb     # Sentiment comparison: Reddit vs YouTube
│   ├── Hypo2.ipynb     # Global events & travel destination discussion
│   └── Hypo3.ipynb     # Co-mention network & community detection
│
├── Datasets/                        # Processed datasets (CSV / JSON / GraphML)
├── Sample Datasets/                 # Smaller sample files for quick testing
│   ├── reddit_sample_dataset.json
│   └── youtube_sample_dataset.csv
│
├── redditClient.py                  # Reddit API authentication helper
├── Reddit_preprocess_sentiment.ipynb
├── assignment2.ipynb
└── sampledata.ipynb
```

---

## Setup

### Prerequisites

- Python 3.8+
- Jupyter Notebook / JupyterLab

### Install dependencies

```bash
pip install praw pandas numpy matplotlib networkx python-louvain vaderSentiment transformers
```

### Configure API credentials

**Reddit (PRAW)**  
Open `redditClient.py` and replace the placeholder values with your own Reddit app credentials:

```python
clientId     = "YOUR_CLIENT_ID"
clientSecret = "YOUR_CLIENT_SECRET"
password     = "YOUR_REDDIT_PASSWORD"
userName     = "YOUR_REDDIT_USERNAME"
```

Create a Reddit app at <https://www.reddit.com/prefs/apps>.

**YouTube Data API**  
Inside `Submission Code (Data Collection)/YouTube_data_collection.ipynb`, set your API key where indicated.

---

## Running the Analysis

Run notebooks in the following order:

1. **Data collection** — `Submission Code (Data Collection)/`  
   Collect raw posts/comments from Reddit and YouTube.

2. **Preprocessing** — `Reddit_preprocess_sentiment.ipynb`  
   Tokenise text and extract country mentions.

3. **EDA** — `Submission Code (Main Analysis)/EDA.ipynb`  
   Explore distributions, top countries, and posting trends.

4. **Hypothesis testing** — run `Hypo1.ipynb`, `Hypo2.ipynb`, `Hypo3.ipynb` in any order.

Pre-collected datasets are in `Datasets/` so steps 1–2 can be skipped if you just want to reproduce the analysis.

---

## Key Datasets

| File | Description |
|------|-------------|
| `combined_unique_reddit_posts.json` | Deduplicated Reddit posts & comments |
| `yt_comments.csv` | YouTube video comments |
| `reddit_county_mentioned_token_df.csv` | Country mentions extracted from Reddit |
| `youtube_county_mentioned_token_df.csv` | Country mentions extracted from YouTube |
| `*_with_date.csv` | Time-stamped variants of the above |
| `graphml_final.zip` | Exported co-mention network graphs |

---

## Methods

- **Sentiment analysis** — VADER and/or transformer-based scoring
- **Country extraction** — token matching against a country name list
- **Network analysis** — NetworkX graph construction; Louvain community detection (`python-louvain`)
- **Statistical testing** — comparing sentiment distributions across platforms and time periods
