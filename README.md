# BBC News Topic Clustering (TF-IDF + MiniBatchKMeans)

This project groups BBC News articles into coherent themes using text-based similarity and clustering techniques.  
It includes an end-to-end NLP pipeline: data cleaning, text preprocessing, TF-IDF feature engineering, clustering, and interpretation.

## Dataset

The dataset is publicly available on Kaggle:

https://www.kaggle.com/datasets/gpreda/bbc-news

- Original dataset: BBC News articles
- Format: CSV
- Working dataset size after cleaning: ~37,000 unique articles

> Note: the dataset consists of short news texts (titles + short descriptions), which naturally increases topic overlap and makes clustering more challenging.

### How to use the dataset

1. Download the dataset from Kaggle.
2. Place the file inside the `data/` folder.
3. Rename it (if needed) to:

```
data/bbc_news.csv
```

The notebook expects the file at this location.

## Repository Structure

```
├── .gitignore
├── README.md
├── requirements.txt
├── notebooks/
│ └── bbc_news_topic_clustering.ipynb
└── data/
└── bbc_news.csv (download separately)
```

## Approach

1. **Data validation and cleaning**
   - verified dataset structure and handled missing values
   - removed duplicate articles
   - parsed and standardized publication dates

2. **Text preprocessing**
   - combined titles and descriptions into a single text field
   - cleaned the text (lowercasing, removing URLs and special characters)
   - filtered out very short documents

3. **Feature engineering**
   - transformed text into TF-IDF vectors
   - compared unigram and bigram representations

4. **Clustering and model selection**
   - applied MiniBatchKMeans for different numbers of clusters
   - evaluated clustering quality using inertia and silhouette score

5. **Cluster analysis and interpretation**
   - examined cluster size distribution
   - analyzed representative and atypical documents
   - extracted top TF-IDF terms per cluster
   - visualized clusters using dimensionality reduction (SVD)

## Results
- The clustering recovers interpretable themes such as sports, politics, global conflicts, and crime.
- One dominant cluster contains broad or mixed news content (expected for short texts).
- Silhouette scores are generally low due to short document length and overlapping vocabulary, but topic-specific clusters show clearer separation.

## How to Run

1. Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows:
```bash
.\.venv\Scripts\activate
```

macOS / Linux:
```bash
source .venv/bin/activate
```

2. Install dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

3. Download the dataset from Kaggle and place it in:

```
data/bbc_news.csv
```

4. Run the notebook:

```bash
jupyter notebook notebooks/bbc_news_topic_clustering.ipynb
```

Then select:

```
Kernel → Restart & Run All
```

to reproduce the full analysis.