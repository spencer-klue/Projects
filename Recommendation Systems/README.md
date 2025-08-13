# Amazon Product Recommendation System — CF & SVD (Notebook)

> Build practical recommenders on the Amazon **Electronics** ratings dataset using popularity baselines, neighborhood methods, and matrix factorization.

This folder contains **`Recommendation Systems (1).ipynb`**, a Jupyter notebook that implements multiple recommendation approaches and compares them on offline metrics.

---

## 🎯 Goals
- Implement **rank-based** (popularity) and **collaborative filtering** recommenders.
- Tune **User–User** and **Item–Item** KNN models and an **SVD** (matrix factorization) model.
- Evaluate with **RMSE**, **Precision@10**, **Recall@10**, and **F1** on a held-out test split.
- Provide helper utilities to:
  - Recommend top-*N* items for a given user
  - Find similar users/items (nearest neighbors)
  - Inspect errors and trade‑offs

---

## 📦 Data
- **Source file (from notebook):** `ratings_Electronics.csv` (Amazon product reviews/ratings; Electronics subset)
- **Columns used:** `user_id`, `prod_id`, `rating` (a `timestamp` column is read but not required for modeling)
- **Prefiltering (as coded):**
  - Keep users with **≥ 50 ratings**
  - Keep items with **≥ 5 ratings**
- **Observed shapes (from this run):**
  - Raw: **(7,824,482, 3)**
  - After filtering: **(65,290, 3)**

> ⚠️ The notebook reads from an **absolute path** in the first cell. Update it to a **relative path** like `data/ratings_Electronics.csv` and place the file accordingly.

---

## 🧠 Methods Implemented
1) **Rank‑Based Recommender** (Popularity)
   - Top‑N items by volume and/or average rating as a sensible cold‑start fallback.
2) **User–User CF (KNNBasic)**  
   - Similarity: **cosine** (tuned)
   - Hyperparameters tuned via Surprise `GridSearchCV`: **k**, **min_k**, **similarity**
3) **Item–Item CF (KNNBasic)**
   - Similarity: **msd** (tuned), compared to cosine
   - Same grid search strategy as User–User
4) **Matrix Factorization (SVD)**
   - Learn **latent factors** from user–item matrix
   - Tuned with grid search over **n_epochs**, **lr_all**, **reg_all**

---

## 📊 Results (this notebook run)

### Cross‑Validation (Grid Search) — best RMSE
- **User–User KNN (cosine):** **0.9701**, params: `k=60, min_k=5, user_based=True`
- **Item–Item KNN (msd):** **0.9753**, params: `k=30, min_k=9, user_based=False`
- **SVD (MF):** **0.8982**, params: `n_epochs=20, lr_all=0.01, reg_all=0.2`

### Held‑Out Test Split
| Model | Settings | RMSE | Precision@10 | Recall@10 | F1 |
|---|---|---:|---:|---:|---:|
| **User–User KNN (baseline)** | cosine | **1.0012** | **0.855** | **0.858** | **0.856** |
| **User–User KNN (tuned)** | cosine, `k=60, min_k=5` | **0.9509** | **0.849** | **0.893** | **0.870** |
| **Item–Item KNN (baseline)** | cosine | **0.9950** | **0.838** | **0.845** | **0.841** |
| **Item–Item KNN (tuned)** | msd, `k=30, min_k=9` | **0.9567** | **0.838** | **0.889** | **0.863** |
| **SVD (baseline)** | default | **0.8882** | **0.853** | **0.880** | **0.866** |
| **SVD (tuned)** | `n_epochs=20, lr_all=0.01, reg_all=0.2` | **0.8808** | **0.854** | **0.878** | **0.866** |

**Takeaways**
- **SVD** achieves the **best RMSE** and strong ranking quality; good general‑purpose recommender.
- **User–User tuned** slightly improves **Recall@10** (great when coverage/recall is prioritized), with small precision trade‑off.
- **Item–Item tuned** improves vs baseline and is useful for **explanations** (“because you liked …”) and related‑items modules.
- Use **Popularity** as a **cold‑start** fallback for new users/items.

> Notes: CV RMSE (grid search) is comparable but not identical to test RMSE since they measure different splits.

---

## ▶️ How to Run
1) Create an environment and install deps:
```bash
python -m venv .venv && source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```
2) Place the dataset at `data/ratings_Electronics.csv` and update the read path in the notebook’s first code cell if needed.  
3) Launch Jupyter and run cells top‑to‑bottom:
```bash
jupyter notebook "Recommendation Systems (1).ipynb"
```

**`requirements.txt` (minimal)**
```
pandas
numpy
scikit-learn
scikit-surprise
matplotlib
seaborn
```

---

## 🧭 Usage Examples (from the notebook)
- **Top‑N for a user:** `get_recommendations(df_final, user_id=<id>, top_n=10, algo=<fitted_model>)`
- **Similar users/items:** neighbor queries using trained KNN models.

> Thresholds used in ranking metrics: **k=10**, **rating ≥ 3.5** considered relevant.

---

## ⚖️ Limitations & Next Steps
- **Cold start:** Popularity & content features (title/category embeddings) can help bootstrap.
- **Bias & Drift:** Popular items/users dominate; monitor over time and add re‑ranking for diversity/novelty.
- **Tuning:** Add more similarity options (Pearson‑baseline), try **BPR/WARP** (implicit feedback) and **LightFM/implicit** for large‑scale.
- **Productionization:** Persist models, add a thin **FastAPI** service, and schedule periodic retraining.

