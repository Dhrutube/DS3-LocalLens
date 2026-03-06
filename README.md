# 🔍 Local Lens: Google Reviews Analytics

**Local Lens** is a data engineering and analytics project designed to transform raw Google Reviews data into actionable business intelligence. By processing large-scale datasets, we aim to recommend business expansion locations based on market density and sentiment, while helping customers identify the best businesses through statistical normalization.

---

## 🏗 Data Infrastructure & Pipeline


The project handles 5GB+ JSON files using a decentralized processing model to prevent memory crashes. 

* **Ingestion:** Utilizes custom `parse()` generators to stream data without loading the entire metadata object.
* **Processing:** Includes sentiment analysis via **VADER**, feature engineering (Chain vs. Independent), and **Z-Score** normalization.
* **Storage:** Flattened CSV files managed via GitHub for version-controlled, BI-ready exports.
* **Presentation:** Exploratory analysis using **Plotly** and executive-facing dashboards in **Tableau** and **Power BI**.

---

## 🛠 Technical Stack

| Category | Tool | Implementation Detail |
| :--- | :--- | :--- |
| **Development** | VS Code | Primary environment for Python/Jupyter scripts. |
| **Analysis** | Python | Pandas, NumPy, and NLTK (VADER) for sentiment. |
| **Visualization** | Plotly | Interactive EDA and trend identification. |
| **BI Reporting** | Tableau | Final interactive dashboards, insights, and recommendations. |
| **Version Control** | GitHub | Managing code, documentation, and version tracking. |
| **Data Ingestion** | Glob | Programmatically grabbing all `.json.gz` files from data folders. |
| **Statistics** | Scikit-Learn | Used `StandardScaler` to normalize scores across different states. |

---

## 📊 Data Schema
We merge two primary datasets to generate our insights:

### Review Datasets
* **user_id**: Unique identifier for the user.
* **rating**: 1-5 star rating.
* **text**: Review of business.
* **gmap_id**: Unique identifier for business.

### Metadata Datasets
* **name**: Name of business.
* **category**: List of relevant business categories.
* **latitude / longitude**: Geographic location of business.
* **price**: Relative price rating ($ to $$$$).

---

## 📈 Roadmap & Progress
* [x] **Phase 1-3:** Setup, Initial EDA, and Goal Definition.
* [/] **Phase 4-6:** Data Cleaning, Feature Engineering (Z-Scores), and Dashboard Prototyping.
* [ ] **Phase 8-10:** Finalizing sentiment word counts, loading state-wide data (TX, CA, NY), and Dino Cage Presentation.

---

## 📂 Directory Structure
```plaintext
├── data/
│   ├── raw/            # Original, untouched data
│   └── processed/      # Cleaned data ready for BI
├── notebooks/          # .ipynb files for EDA and Plotly
├── src/                # .py scripts for data pipelines
├── outputs/            # Exported charts and PDF reports
└── README.md           # Project entry point
