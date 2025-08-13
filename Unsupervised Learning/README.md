# Unsupervised Learning — Clustering & Dimensionality Reduction (Notebook)


>
Discover structure in unlabeled data using clustering (KMeans/DBSCAN/Agglomerative) and dimensionality reduction (PCA/TSNE). This notebook explores modeling choices, evaluates cluster quality, and visualizes segments for downstream use (e.g., marketing personas, anomaly screening).

## Data
- Loaded from: `/Users/spenc/Programming/DS/Unsupervised Learning CS/marketing_campaign.csv", sep="\t`


## Methods
- **Scaling:** `StandardScaler` before clustering to normalize feature ranges.
- **KMeans** (k tried: 4): baseline partitioning; elbow/silhouette to pick k.


## Evaluation
- **Silhouette score** (higher is better)
- **Davies–Bouldin index** (lower is better)
- **Calinski–Harabasz index** (higher is better)


## Visualizations
- PCA/t‑SNE scatter plots colored by cluster labels
- Elbow & silhouette‑analysis plots
- Dendrogram (if hierarchical used)
- Cluster profile heatmaps (feature means by cluster)


## How to Run
1) Create an environment and install deps:
```bash
python -m venv .venv && source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```
2) Place your dataset at `data/input.csv` and update the read path in the first code cell if needed.
3) Launch Jupyter and run cells top‑to‑bottom:
```bash
jupyter notebook "Unsupervised Learning.ipynb"
```

**`requirements.txt` (minimal)**
```
pandas
numpy
scikit-learn
matplotlib
seaborn
```

## Interpreting Clusters
- **Size & purity:** ensure clusters are meaningful (avoid micro‑clusters).
- **Profiles:** summarize means/medians per feature by cluster; name your segments (e.g., "High‑engagement, Low‑spend").
- **Actionability:** attach recommended plays (targeted campaigns, AB tests) to each segment.
- **Stability:** test sensitivity to random seeds and parameters (k, eps, min_samples).


## Notes & Limitations
- Results depend on scaling and pre‑filters; keep a pipeline for reproducibility.
- For high‑dimensional sparse data, consider **TruncatedSVD**/**UMAP**.
- Re‑evaluate segment definitions as new data arrives (drift).

---

### Detected from this notebook
- **Data sources:** /Users/spenc/Programming/DS/Unsupervised Learning CS/marketing_campaign.csv", sep="\t
- **Algorithms/Tools:** KMeans, StandardScaler, silhouette_score
- **KMeans k-values tried:** 4
