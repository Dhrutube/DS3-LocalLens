# 🔍 Local Lens: Google Reviews Analytics

**Local Lens** is a data engineering and analytics project designed to transform raw Google Reviews data into actionable business intelligence. By processing large-scale datasets, we aim to recommend business expansion locations based on market density and sentiment, while helping customers identify the best businesses through statistical normalization.

The final product is an interactive Tableau dashboard that gives customers and businesses a new lens through which to search for their next meal or decide where to locate across two different cities.

**Live Dashboard**: ___________addlink___________

---
## Data Collection

This project used multiple data sources

1. **Mcauleylab.ucsd.edu Google Local Data (2021):** A web-scraped dataset containing individual review data and aggregate review trends for every business in every state in the United States.
   - Metadata:
  


### Metadata Datasets

* **name**: Name of business.
* **category**: List of relevant business categories.
* **latitude / longitude**: Geographic location of business.
* **price**: Relative price rating ($ to $$$$).
   - Review Data:

### Review Datasets

* **user_id**: Unique identifier for the user.
* **rating**: 1-5 star rating.
* **text**: Review of business.
* **gmap_id**: Unique identifier for business.

2. **simplemaps.com United States Cities Database:** City longitude and latitude as well as population statistics.
   - (fill in )

3. **The complete google business categories list (updated 2025)**: A dataset dividing complex google categories into subcategories and main larger categories for data set grouping.
   - (filll in)




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

## Tableau Dashboard

1. The Customer Lens
   -

2. The Business lens
   -

## Accessing the Dashboard

___link to tableau public.com____


# How to use the customer lens


# How to use the Business lens
   ## Filter:
1. State: Select the state you want to analyze.
2. City: Choose a city within the selected state to focus on a more specific local market.
3. Broad Category: Select the business category you want to explore

   ## Chart:
For the map: The map visualization shows the geographic distribution of businesses based on the opportunity score. 
Colors represent the opportunity score, allowing users to quickly identify areas where business opportunities may be higher. This helps users understand where potential market opportunities are concentrated geographically.

For the Bar Chart:
   + Top Categories: The Top Categories chart ranks business industries based on their average opportunity score.
   => This helps identify: which industries may have stronger market potential and which categories appear to have higher opportunity overall.
   + Top Cities: The Top Cities chart ranks cities based on their average opportunity score.
   => This helps users understand: which cities may provide better business opportunities and how opportunity varies across different locations.

For the Scatter Plot: compares opportunity and competition for businesses.

    + X-axis: Competition Score
    + Y-axis: Opportunity Score
    The chart is divided into four quadrants using average values, which represent different market conditions.
       
     Top-left: high opportunity score and low competition => Good market for new businesses.
     Top-right: high opportunity score and high comptetition => Strong market but competitive.
     Bottom-left: low opportunity score and low competition => Weak market with low demand.
     Bottom-right: low opportunity score and high competition => Saturated market with many competitors.

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




















