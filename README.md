# 🔍 Local Lens: Google Reviews Analytics

[cite_start]**Local Lens** is a data engineering and analytics project designed to transform raw Google Reviews data into actionable business intelligence[cite: 9]. [cite_start]By processing large-scale datasets, we aim to recommend business expansion locations based on market density and sentiment, while helping customers identify the best businesses through statistical normalization[cite: 10, 11].

---

## 🏗 Data Infrastructure & Pipeline
[cite_start]The project handles 5GB+ JSON files using a decentralized processing model to prevent memory crashes[cite: 15].

* [cite_start]**Ingestion:** Utilizes custom `parse()` generators to stream data without loading the entire metadata object[cite: 16, 17].
* [cite_start]**Processing:** Includes sentiment analysis via **VADER**, feature engineering (Chain vs. Independent), and **Z-Score** normalization[cite: 21, 22, 23].
* [cite_start]**Storage:** Flattened CSV files managed via GitHub for version-controlled, BI-ready exports[cite: 27, 29, 31].
* [cite_start]**Presentation:** Exploratory analysis using **Plotly** and executive-facing dashboards in **Tableau** and **Power BI**[cite: 33, 35, 36].

---

## 🛠 Technical Stack

| Category | Tool | Implementation Detail |
| :--- | :--- | :--- |
| **Development** | VS Code | [cite_start]Primary environment for Python/Jupyter scripts[cite: 38]. |
| **Analysis** | Python | [cite_start]Pandas, NumPy, and NLTK (VADER) for sentiment[cite: 38]. |
| **Visualization** | Plotly | [cite_start]Interactive EDA and trend identification[cite: 38]. |
| **BI Reporting** | Tableau | [cite_start]Final interactive dashboards, insights, and recommendations[cite: 38]. |
| **Version Control** | GitHub | [cite_start]Managing code, documentation, and version tracking[cite: 38]. |
| **Data Ingestion** | Glob | [cite_start]Programmatically grabbing all `.json.gz` files from data folders[cite: 38]. |
| **Statistics** | Scikit-Learn | [cite_start]Used `StandardScaler` to normalize scores across different states[cite: 38]. |

---

## 📊 Data Schema
We merge two primary datasets to generate our insights:

### Review Datasets
* [cite_start]**user_id**: Unique identifier for the user[cite: 41].
* **rating**: 1-5 star rating[cite: 41].
* [cite_start]**text**: Review of business[cite: 41].
* [cite_start]**gmap_id**: Unique identifier for business[cite: 41].

### Metadata Datasets
* [cite_start]**name**: Name of business[cite: 43].
* [cite_start]**category**: List of relevant business categories[cite: 43].
* [cite_start]**latitude / longitude**: Geographic location of business[cite: 43].
* [cite_start]**price**: Relative price rating ($ to $$$$)[cite: 43].

---

## 📈 Roadmap & Progress
* [cite_start][x] **Phase 1-3:** Setup, Initial EDA, and Goal Definition[cite: 45, 46, 47].
* [cite_start][/] **Phase 4-6:** Data Cleaning, Feature Engineering (Z-Scores), and Dashboard Prototyping[cite: 48, 50, 52].
* [cite_start][ ] **Phase 8-10:** Finalizing sentiment word counts, loading state-wide data (TX, CA, NY), and Dino Cage Presentation[cite: 56, 58, 59].

---

## 📂 Directory Structure
```plaintext
├── data/
[cite_start]│   ├── raw/            # Original, untouched data [cite: 63]
[cite_start]│   └── processed/      # Cleaned data ready for BI [cite: 64]
[cite_start]├── notebooks/          # .ipynb files for EDA and Plotly [cite: 65]
[cite_start]├── src/                # .py scripts for data pipelines [cite: 66]
[cite_start]├── outputs/            # Exported charts and PDF reports [cite: 67]
[cite_start]└── README.md           # This document [cite: 68]

