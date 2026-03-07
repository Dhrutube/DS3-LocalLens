# 🔍 Local Lens: Google Reviews Analytics

**Local Lens** is a data engineering and analytics project designed to transform raw Google Reviews data into actionable business intelligence. By processing large-scale datasets, we aim to recommend business expansion locations based on market density and sentiment, while helping customers identify the best businesses through statistical normalization.

The final product is an interactive Tableau dashboard that gives customers and businesses a new lens through which to search for their next meal or decide where to locate across two different cities.

---

# Accessing the Dashboard

👉 **Live Tableau Dashboard:**  
https://public.tableau.com/shared/XMMQ7FD7R?:display_count=n&:origin=viz_share_link

---
## Data Collection

This project uses multiple datasets from external sources.

## Google Local Data – McAuley Lab (UC San Diego)

Source:  
https://mcauleylab.ucsd.edu/public_datasets/gdrive/googlelocal/

This dataset contains web-scraped Google Maps review data and business metadata across the United States.

### Metadata Fields

- **name** – Name of the business  
- **category** – List of associated Google business categories  
- **latitude / longitude** – Geographic location of the business  
- **price** – Relative price rating ($ to $$$$)

### Review Data

- **user_id** – Unique identifier for the user  
- **rating** – Star rating (1–5)  
- **text** – Customer review text  
- **gmap_id** – Unique identifier for the business

---

## United States Cities Database

Source:  
https://simplemaps.com/data/us-cities

This dataset provides geographic information about U.S. cities, including:

- city name  
- latitude and longitude  
- population statistics  

It was used to match businesses to the **closest city location** using geographic coordinates.

---

## Google Business Categories Dataset

Source:  
https://www.lobstr.io/blog/google-business-categories

This dataset provides a structured list of Google Business categories and was used to group complex Google categories into **broader standardized categories** for analysis.

---

## Data Processing and Feature Engineering

* **Processing:** Includes sentiment analysis via **VADER**, feature engineering (Chain vs. Independent), and **Z-Score** normalization.
* **Storage:** Flattened CSV files managed via GitHub for version-controlled, BI-ready exports.
(add more)

## Sentiment Analyis (TF-IDF)

1. Review Segmentation
      * Reviews were grouped based on:
         * Area type: Urban, Suburban, Rural
         * Business type: Restaurant vs. Non-Restaurant
         * Sentiment group: Positive reviews vs. Negative reviews (based on star ratings)
      * This segmentation allowed us to compare how customer priorities differ across geographic and business contexts.

2. Text Processing
      * Extracted bigrams (two-word phrases) to capture more meaningful expressions such as “fast service” or “friendly staff”
      * We used TF-IDF (Term Frequency–Inverse Document Frequency) to identify phrases that were important within each review group.

3. Extracting Key Themes
      * For each segment (e.g., Urban Restaurants – Positive Reviews), we computed the top 20 bigrams with the highest TF-IDF scores. These phrases represent themes that frequently appear in that segment's reviews while remaining distinctive compared to other reviews.
         * Examples of extracted phrases include: fast service, friendly staff, slow service
         * These phrases were then compiled into a dataset used for visualization in Tableau.

---

# Tableau Dashboard

The final Tableau dashboard provides multiple analytical perspectives on the dataset.

---

# The Customer Lens

## Overview

The **Customer Lens** focuses on understanding customer behavior and satisfaction across different businesses and locations.

This view allows users to explore how customers interact with businesses based on reviews, ratings, and geographic distribution.

---

## Map Visualization

The map displays businesses geographically using latitude and longitude coordinates.

Each point represents a business.

- **Color:** Selected competition or relative score metric
- **Size:** Number of reviews

Larger circles indicate businesses that receive more customer reviews.

This helps identify areas with **high customer engagement and varying competition levels**.

---

## Filters

Users can interact with the dashboard using:

- **Choose Category** – analyze specific industries
- **Choose City** – focus on specific local markets
- **Choose State** – explore regional trends

---
## Metric Selector

Users can switch between several metrics:

- **Niche Competition Score**
- **Broad Competition Score**
- **Overall Category Relative Score**
- **Overall City Relative Score**

This allows exploration of different perspectives on competition and demand.


---

# The Business Lens

## Overview

The **Business Lens** focuses on identifying potential market opportunities for businesses across locations and industries.

It helps evaluate where new businesses may have stronger opportunities based on **opportunity scores and competition levels**.

---

## Map Visualization

The map shows the geographic distribution of businesses across selected states.

- **Color:** Average opportunity score
- **Size:** Concentration of businesses

This highlights regions where **market opportunities may be stronger**.

---

## Filters

- **State** – filter by geographic region
- **City** – focus on local markets
- **Broad Category** – analyze specific industries

---

## Opportunity vs Competition Scatter Plot

The scatter plot compares **opportunity scores and competition levels**.

- **X-axis:** Competition Score  
- **Y-axis:** Opportunity Score  

The chart is divided into four quadrants based on average values.

### Quadrant Interpretation

**Top-left**  
High opportunity + low competition  
→ Good market for new businesses

**Top-right**  
High opportunity + high competition  
→ Strong but competitive market

**Bottom-left**  
Low opportunity + low competition  
→ Weak market with low demand

**Bottom-right**  
Low opportunity + high competition  
→ Saturated market

---

# Review Volatility

## Filters

Users can explore review volatility using:

- **Regions:** Rural, Suburban, Urban
- **Business Categories:** Top 10 most frequent categories
- **Metrics:** Selected comparison metric

---

## Charts

### Map

Hover over a state to see summary metrics and click to update the volatility chart.

### Line Chart

The line chart groups businesses into **bins based on number of reviews** and shows the **top 10 categories per state** based on review volatility.

This allows comparison of **how stable or volatile customer feedback is across categories and regions**.

---


UPDATE this
|
|
|
V
## 📂 Repostiory Structure
```plaintext
├── data/
│   ├── raw/            # Original, untouched data
│   └── processed/      # Cleaned data ready for BI
├── notebooks/          # .ipynb files for EDA and Plotly
├── src/                # .py scripts for data pipelines
├── outputs/            # Exported charts and PDF reports
└── README.md           # Project entry point
```

## Technical Stack

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

## Key Insights 


---


## Future Enhancements

---

## Project information

## Citation:
1. Li, J. (n.d.). Google Local review data. https://mcauleylab.ucsd.edu/public_datasets/gdrive/googlelocal/

2. The complete Google Business Categories list [Updated 2025]. (2024, November 6). https://www.lobstr.io/blog/google-business-categories

## Roadmap & Progress
* [x] **Phase 1-3:** Setup, Initial EDA, and Goal Definition.
* [/] **Phase 4-6:** Data Cleaning, Feature Engineering (Z-Scores), and Dashboard Prototyping.
* [ ] **Phase 8-10:** Finalizing sentiment word counts, loading state-wide data (TX, CA, NY), and Dino Cage Presentation.

---































