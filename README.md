# Amazon vs Walmart Product Analysis
This repository contains notebooks and data for comparing Amazon and Walmart product listings.
Where images are saved
- Generated PNG charts are saved to `figures/generated_images/` by default (this folder is ignored by git).
- Only `figures/outliers.csv` is tracked in version control. PNG files are generated locally and not committed by default.

To keep images out of the repository but retain the anomaly CSV, this project uses a dedicated generated-images folder (`figures/generated_images/`) and a `.gitignore` entry that ignores that folder while explicitly keeping `figures/outliers.csv` tracked.

---

## 📌 Project Overview
This repository contains code and data to compare product catalogs from Amazon and Walmart. The notebooks clean and preprocess raw data, perform exploratory data analysis (EDA), surface anomalies, and create presentation-ready visualizations.

---

## 🎯 Project Objectives
1. Ingest and standardize raw CSVs from Amazon and Walmart
2. Clean and deduplicate records to create a single canonical dataset
3. Handle missing values and normalize numeric types
4. Detect and extract anomalous records (outliers) for review
5. Produce clear EDA visualizations and executive conclusions
6. Provide a lightweight, reproducible workflow for regenerating outputs

---

## 📂 Dataset (columns of interest)
The cleaned dataset (`cleaned_amazon_walmart_data.csv`) includes these primary columns:

| Column | Description |
|--------|-------------|
| `platform` | Source platform (`Amazon` or `Walmart`) |
| `final_price` | Selling price (numeric) |
| `initial_price` | List/original price (numeric) |
| `discount` | Discount amount in USD (numeric) |
| `rating` | Customer rating (1.0–5.0) |
| `brand` | Product brand |
| `categories` | Category string |
| `currency` | Currency code |
| `description` | Text description |

---

## 🧹 Data cleaning & preprocessing (what the cleaning notebook does)
- Standardizes column names and types
- Removes irrelevant columns (`ingredients`, `upc`, `url`) where present
- Converts `final_price`, `initial_price`, `discount`, `rating` to numeric (with safe coercion)
- Fills missing `brand`, `currency`, and `description` with safe defaults
- Replaces invalid/zero `rating` values with a conservative value (as implemented in the notebook)
- Deduplicates on key columns (platform, brand, final_price, initial_price, discount, rating, description)
- Detects outliers by: price z-score (|z| > 3) and discount >= 99th percentile
- Exports cleaned dataset and anomaly CSV

---

## 📈 Visualizations (12 charts)
The visualization notebook and the PNG export notebook create these 12 visual outputs:

1. Rating distribution (histogram + KDE)
2. Price comparison by platform (boxplot)
3. Rating vs final price (scatter)
4. Correlation heatmap (final_price, initial_price, rating, discount)
5. Average price by platform (bar)
6. Discount distribution panels (Amazon vs Walmart histograms)
7. Initial vs final price (scatter with "no discount" line)
8. Product distribution by platform (pie)
9. Rating category distribution (bar)
10. Rating distribution by platform (violin)
11. Average discount by platform (bar)
12. Final price combined visualization (density by platform + boxplot, clipped to 99th percentile)

Additionally: histograms, boxplots, KDEs, violin plots and pie charts are used across these visuals.

---

## 📦 Output files and where to find them
- `figures/outliers.csv` — Combined list of extracted anomalies (price and/or discount). This file is tracked in the repository for review.
- PNG images (high-resolution, 300 DPI) — created locally and saved to the `figures/` folder when you run the export notebook. These PNGs are not tracked by default to avoid large binary files in git.

Current `figures/` contents (tracked):

```
figures/
└─ outliers.csv
```

---

## 🔄 Recommended workflow (3 notebooks)
Follow this order for reproducibility and clarity — each step is small and explicit.

1) Data cleaning — `data_cleaning_analysis.ipynb` (run interactively in Jupyter)

- Purpose: read raw CSVs, clean, deduplicate, detect outliers, and write `cleaned_amazon_walmart_data.csv` and `figures/outliers.csv`.
- Note: run this notebook interactively (open in Jupyter and run all cells); it will create `outliers.csv` as part of its pipeline (no separate command required).

2) Visualization — `visualization.ipynb` (interactive)

- Purpose: load `cleaned_amazon_walmart_data.csv` and explore the 12 charts with inline conclusions. This notebook is presentation-focused and does not write PNGs.

3) PNG export — `export_png_images.ipynb` (optional; run when you need image files)

- Purpose: generate the 12 visualization PNG files at 300 DPI into `figures/`.
- To export programmatically (optional), run:

```bash
jupyter nbconvert --to notebook --execute export_png_images.ipynb
```

---

## 🔍 Key findings (summary)
- Amazon products are, on average, higher priced than Walmart in this dataset.
- Walmart products show higher average ratings in the cleaned dataset.
- More than half of products have zero discount; discount behavior differs by platform.
- Final and initial price are strongly correlated; discounts are relatively sparse but can be large for a few products.

### Additional observations
- A large share of Amazon items report zero or negligible discounts, while Walmart shows more active discounting behavior for a subset of products.
- A small number of extreme discounts and prices substantially affect mean statistics; median and percentile-based summaries are provided in the notebooks to reduce sensitivity to these extremes.

---

## ⚠️ Limitations
- Some ratings were missing or imputed; this can bias aggregated statistics.
- Categories and descriptions contain noisy free text; downstream grouping may need additional cleaning.
- A small number of extreme price values influence mean estimates; visualizations clip at the 99th percentile when appropriate.

---

## ⚙️ Quick start
1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Run the cleaning notebook interactively (open `data_cleaning_analysis.ipynb` in Jupyter and run all cells).

3. Open `visualization.ipynb` to inspect charts and conclusions.

4. (Optional) Export PNGs:

```bash
jupyter nbconvert --to notebook --execute export_png_images.ipynb
```

---

👨‍💻 Author

Vishnuraj M

Data Analyst | Full Stack Developer | Machine Learning

- 🌐 Portfolio: https://portfolio-reactjs-tensor-flow-wiy9.vercel.app
- 💼 LinkedIn: https://linkedin.com/in/vishnurajagopalan-pixel
- 📧 Email: vishnurajagopalanmannilvr@gmail.com
- 🐙 GitHub: https://github.com/Vishnu-beep-hub