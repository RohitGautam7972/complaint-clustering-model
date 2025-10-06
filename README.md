# Complaint Clubbing Pipeline

A **single-file prototype** implementing a **Complaint Clubbing Pipeline**, designed for **clarity, experimentation, and easy iteration**.  
This pipeline helps cluster similar complaints based on textual content, keywords, and category information.

---

## ✨ Features

### 1. Data Handling
- **CSV Loader:** Easily load complaint datasets.
- **Synthetic Data Generator:** Quickly test clustering logic without a real dataset.

### 2. Preprocessing
- Basic text cleaning:
  - Lowercasing
  - Punctuation removal
  - Stopwords removal
- Optional **lemmatization** via NLTK for better word normalization.

### 3. Embedding & Similarity
- **Sentence-BERT embeddings** (`all-MiniLM-L6-v2`) for semantic similarity.
- **Pairwise cosine similarity** between complaints.
- **Keyword overlap** via Jaccard similarity on top-N tokens.
- **Final similarity score:** Weighted sum of text, keyword, and category similarity.

### 4. Dynamic Thresholding
- Adjustable threshold function for pairwise similarity.
- Can be tuned for sensitivity in clustering.

### 5. Custom Clustering
- **Incremental connected-components algorithm**.
- Supports **time window constraint** (e.g., cluster complaints only within 30 days).
- **Post-processing**:
  - Merge closely related clusters
  - Split loose clusters for better precision.

### 6. Cluster Insights
- **Confidence score**: Mean pairwise similarity within cluster.
- **Representative complaint selection**: Longest complaint + most recent as tie-breaker.
- **Keyword extraction**: Using YAKE for meaningful summaries.

### 7. Evaluation
- **Silhouette score** (for >1 cluster) to evaluate cluster cohesion.
- **Purity** score (requires ground truth categories).

### 8. Serving
- FastAPI scaffold ready for production deployment.

---

## 📦 Installation

```bash
# Clone repository
git clone <your-repo-url>
cd complaint-clubbing

# Create virtual environment
python -m venv venv
source venv/bin/activate   # Linux / Mac
venv\Scripts\activate      # Windows

# Install dependencies
pip install -r requirements.txt
