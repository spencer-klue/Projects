# ExtraaLearn — Lead Conversion Classification (Notebook)

> Predict which leads are likely to convert and surface the drivers behind conversion for an EdTech funnel.

This repository contains the notebook **`Classification.ipynb`** that builds and evaluates classification models on the ExtraaLearn leads dataset.

---

## 🧠 Problem
Given historic lead interactions (web/app behavior, channels, last activity, profile completion, etc.), predict **`status`** (1 = converted, 0 = not converted) so Sales/Marketing can prioritize outreach and tailor nurture flows.

---

## 📦 Data (from project brief)
Each row = one lead.

**Target**
- `status` — 1 if converted to paid, 0 otherwise

**Key features**
- `age`, `website_visits`, `time_spent_on_website`, `page_views_per_visit`
- `current_occupation` ∈ {Professional, Unemployed, Student}
- `first_interaction` ∈ {Website, Mobile App}
- `profile_completed` ∈ {Low (0–50%), Medium (50–75%), High (75–100%)}
- `last_activity` (Email / Phone / Website subtypes)
- Channel flags: `print_media_type1`, `print_media_type2`, `digital_media`, `educational_channels`, `referral`

> ⚠️ The notebook currently reads the CSV from an absolute path. **Update the path in the first data cell** to a relative one (e.g., `data/ExtraaLearn.csv`) or place the file accordingly.

---

## 🔍 What’s in the notebook
- **EDA**
  - Category distributions and conversion rates
  - Numeric vs target plots & correlation heatmap
  - Confusion-matrix visualizations
- **Preprocessing**
  - `pd.get_dummies(drop_first=True)` for categorical encoding
  - Train/test split (70%/30%, `random_state=1`)
- **Models & Tuning**
  - Baseline: `DecisionTreeClassifier`
  - Tuned Decision Tree (`GridSearchCV`, scorer = **recall** of positive class)
  - Tuned Random Forest (`GridSearchCV`, scorer = **recall** of positive class)
  - Class weights tried (e.g., `{0: 0.3, 1: 0.7}`) to handle imbalance
- **Evaluation**
  - `classification_report` (precision/recall/F1/support)
  - Confusion matrices
  - Feature importance plots (tree-based models)

---

## 📈 Results (from notebook outputs)
**Test set**
- **Baseline Decision Tree** – *Accuracy*: **0.81**, *Recall (class 1)*: **0.70**, *Precision (class 1)*: **0.69**
- **Tuned Random Forest** – *Accuracy*: **0.84**, *Recall (class 1)*: **0.85**, *Precision (class 1)*: **0.69**

> Interpretation: the tuned RF significantly improves **recall for converters** (1) — useful when you’d rather **not miss** potentially good leads (sales capacity permitting), at the cost of some precision.

---

## 🗂 Recommended repo layout (optional)
If you split the notebook into a small project, use:
```
.
├─ data/
│  └─ ExtraaLearn.csv              # (not committed if private)
├─ notebooks/
│  └─ Classification.ipynb
├─ reports/
│  └─ figures/                     # exported plots
├─ src/                            # (optional) turn notebook into scripts
│  ├─ train.py
│  └─ score.py
└─ README.md
```

---

## ▶️ How to run
1) Create an environment and install deps:
```bash
python -m venv .venv && source .venv/bin/activate     # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```
2) Put the dataset at `data/ExtraaLearn.csv` **or** update the read path in the notebook’s first data cell.
3) Open Jupyter and run the notebook cells top-to-bottom:
```bash
jupyter notebook notebooks/Classification.ipynb
```
4) (Optional) Export figures to `reports/figures/` for your GitHub README or slides.

**`requirements.txt` (minimal)**
```
pandas
numpy
scikit-learn
matplotlib
seaborn
```

---

## 🧭 Business takeaways (summarize after you re-run on your data)
- High **profile completion** and stronger **on-site engagement** are associated with higher conversion.
- **Website-first** interactions tend to convert better than **mobile-app-first** interactions in this dataset.
- **Referrals / educational channels** often indicate warmer intent.
- Choose thresholds based on **sales capacity** (optimize for Precision@K or Recall@K as needed).

---

## ⚖️ Notes & limitations
- Historical-data bias may reflect past outreach/UX; monitor drift and fairness.
- Calibrate thresholds to match business KPIs (e.g., daily call quota).
- Re-run tuning periodically as campaigns/traffic mix change.

---

## 📜 License
MIT (or your preference) — add a `LICENSE` file if you plan to share/reuse.

