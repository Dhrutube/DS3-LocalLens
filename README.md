# 🔍 Local Lens: Google Reviews Analytics

[cite_start]**Local Lens** is a data engineering and business intelligence project designed to transform raw Google Reviews data into actionable insights for business expansion and consumer decision-making[cite: 9].

---

## 📍 Project Overview
Our team is tackling the challenge of "rating inflation" and geographic data density to answer two core questions:
1. [cite_start]**Business Strategy:** How do we recommend where businesses should locate based on market gaps? [cite: 10]
2. [cite_start]**Consumer Insight:** How do we help customers choose the best company by normalizing "harsh" vs. "easy" review cultures? [cite: 11, 24]

## 🏗 Data Infrastructure & Pipeline


[cite_start]To handle large-scale datasets (5GB+ JSON files) without memory crashes, we implemented a decentralized processing model[cite: 13, 15]:

* [cite_start]**Ingestion:** Used custom `parse()` generators to stream data and filter for specific columns (`gmap_id`, `rating`, `text`) without loading entire metadata objects[cite: 16, 17].
* [cite_start]**Processing:** * **Sentiment Analysis:** Utilized **VADER** to generate "Compound Scores" for review text[cite: 19, 21].
    * [cite_start]**Feature Engineering:** Created `Is_Brand` (Chain vs. Independent) and `Urban_Rural` tags[cite: 22].
    * [cite_start]**Statistical Normalization:** Applied `StandardScaler` to calculate **Z-Scores**, allowing fair comparisons across different regions[cite: 23, 24].
* [cite_start]**Storage:** Flattened nested JSON data into optimized CSV tables for faster BI loading[cite: 29, 30].

## 🛠 Technical Stack
| Category | Tool | Implementation Detail |
| :--- | :--- | :--- |
| **Development** | VS Code | [cite_start]Environment for Python and Jupyter Notebooks[cite: 38]. |
| **Analysis** | Python | [cite_start]Pandas, NumPy, and NLTK (VADER)[cite: 38]. |
| **Normalization** | Scikit-Learn | [cite_start]`StandardScaler` for cross-state score normalization[cite: 38]. |
| **Visualization** | Plotly | [cite_start]Interactive EDA and distribution visualizations[cite: 38]. |
| **BI Reporting** | Tableau/Power BI | [cite_start]Final interactive executive dashboards[cite: 38]. |
| **Version Control** | GitHub | [cite_start]Managing code, documentation, and data versions[cite: 31, 38]. |

## 📊 Data Schema
We utilize two primary datasets provided by Google Reviews:
* [cite_start]**Review Data:** `user_id`, `rating`, `text`, `time`, and `gmap_id`[cite: 41].
* [cite_start]**Metadata:** Business `name`, `category`, `latitude/longitude`, `price` level, and `state` status[cite: 43].

## 📈 Roadmap & Progress
- [x] [cite_start]**Phase 1-3:** Repository initialization and project direction[cite: 45, 47].
- [x] [cite_start]**Phase 4-5:** Data cleaning, outlier handling, and Z-score implementation[cite: 48, 50].
- [ ] [cite_start]**Phase 6-8:** Dashboard creation in Tableau and "Review Culture" parameter updates[cite: 52, 56].
- [ ] [cite_start]**Phase 9-10:** Finalizing state-specific datasets (TX, CA, NY) and Dino Cage Presentation preparation[cite: 58, 59].

## 📂 Directory Structure
```text
├── data/
│   ├── raw/            # Original, untouched data [cite: 63]
│   └── processed/      # Cleaned data ready for Power BI [cite: 64]
├── notebooks/          # .ipynb files for EDA and Plotly [cite: 65]
├── src/                # .py scripts for data pipelines [cite: 66]
├── outputs/            # Exported charts and PDF reports [cite: 67]
├── README.md           # Project entry point [cite: 68]
└── DESIGN_DOC.md       # Full design documentation [cite: 69]
