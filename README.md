## Complaint Clubbing Pipeline

A single-file prototype that implements the complaint clubbing roadmap — designed for clarity, experimentation, and easy iteration.

✨ Features

Data Handling

CSV loader and synthetic data generator for testing

Preprocessing

Basic text cleaning (lowercasing, punctuation removal, stopwords)

Optional lemmatization (via NLTK)

Embedding & Similarity

Sentence-BERT embeddings (all-MiniLM-L6-v2)

Pairwise cosine similarity

Keyword overlap (Jaccard similarity on top-N tokens)

Final score = weighted sum of text, keyword, and category similarity

Dynamic Thresholding

Adjustable per-pair threshold function

Custom Clustering

Incremental connected-components style algorithm

Time window constraint (e.g., group only complaints within 30 days)

Postprocessing: merge close clusters, split loose ones

Cluster Insights

Confidence score (mean pairwise similarity)

Representative complaint selection (longest + most recent tie-breaker)

Keyword extraction (YAKE)

Evaluation

Silhouette score (if >1 cluster)

Purity (based on ground truth categories)

Serving

FastAPI endpoint scaffold for productionization
