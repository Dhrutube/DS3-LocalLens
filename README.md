# 🔍 Local Lens: Google Reviews Analytics

**Local Lens** is a data engineering and analytics project designed to transform raw Google Reviews data into actionable business intelligence. By processing large-scale datasets, we aim to recommend business expansion locations based on market density and sentiment, while helping customers identify the best businesses through statistical normalization.

The final product is an interactive Tableau dashboard that gives customers and businesses a new lens through which to search for their next meal or decide where to locate across two different cities.

---

# Accessing the Dashboard

👉 **Live Tableau Dashboard:**  
https://public.tableau.com/views/your-dashboard-link

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

# Tableau Dashboard

## The Customer Lens
   ### Overview: 
The Customer Lens focuses on understanding customer behavior and satisfaction across different businesses and locations. This view allows users to explore how customers interact with businesses based on reviews, ratings, and geographic distribution.
   ### Map Visualization:
   + The map displays businesses geographically using latitude and longitude coordinates. Each point on the map represents an individual business.
   + Color indicates the competition score (or selected metric), helping highlight areas with higher or lower competition.
   + Size represents the number of reviews
   + Larger circles indicate businesses that receive more customer reviews.

This visualization helps users identify areas with highly reviewed businesses and varying levels of competition.
   ### Filters
Users can interact with the dashboard using the following filters:
   + Choose Category – Allows users to select specific business categories to analyze customer activity within those industries.
   + Choose City – Filters the map to focus on specific cities.
   + Choose State – Filters the data by state to explore regional patterns.
These filters allow users to narrow the analysis to specific markets and industries.

   ### Metric Selector
A dropdown menu allows users to switch between different metrics used to evaluate business environments:
   + Niche Competition Score – Measures competition within more specific business niches.
   + Broad Competition Score – Measures competition across broader business categories.
   + Overall Category Relative Score – Compares a business category’s performance relative to others.
   + Overall City Relative Score – Compares city-level performance across different locations.

This feature enables users to explore multiple perspectives on competition and market performance.

   ### Purpose
The Customer Lens helps users understand where customers are actively engaging with businesses and how customer activity varies across locations and industries. By combining review counts, geographic distribution, and competition metrics, this view provides insight into customer demand and competitive landscapes.

## The Business lens
   ### Overiew
The Business Lens focuses on identifying potential market opportunities for businesses across different locations and industries. This dashboard helps users evaluate where new businesses may have stronger opportunities based on opportunity scores and competition levels.   
   ### Map Visualization
The map shows the geographic distribution of businesses across selected states.
   + Each circle represents aggregated business activity within a location.
   + Color represents the average opportunity score, allowing users to quickly identify areas with stronger or weaker business opportunities.
   + Size represents the relative concentration of businesses or activity in that location.
This visualization helps highlight regions where market opportunities may be stronger for new businesses.
   ### Filters
The dashboard includes interactive filters that allow users to explore the data from different perspectives:
   + State: Filter results by geographic region.
   + City: Focus on specific local markets.
   + Choose Category: Analyze business opportunities within specific industries.

These filters allow users to dynamically explore how opportunity and competition vary across different locations and business categories.


   ### Opportunity vs Competition Scatter Plot

## Accessing the Dashboard

___link to tableau public.com____
## How to Use the Customer Lens

### Filters
- **Choose Category:** Select specific business categories to analyze customer activity within those industries.
- **Choose City:** Focus on specific cities.
- **Choose State:** Filter the data by state to explore regional patterns.

### Map
The map displays businesses geographically using latitude and longitude coordinates.  
Each point represents a business.

- **Color:** Indicates the selected competition or relative score metric.
- **Size:** Represents the number of reviews (customer engagement).

This helps identify areas with high customer activity and varying competition levels.

### Metric Selector
Users can switch between several metrics:

- **Niche Competition Score**
- **Broad Competition Score**
- **Overall Category Relative Score**
- **Overall City Relative Score**

These metrics allow users to explore different perspectives on competition and market performance.

---

## How to Use the Business Lens

### Filters
- **State:** Select the state you want to analyze.
- **City:** Choose a city within the selected state to focus on a specific local market.
- **Broad Category:** Select the business category you want to explore.

### Charts

#### Map
The map shows the geographic distribution of businesses based on the **opportunity score**.

- **Color:** Opportunity score
- **Size:** Relative concentration of businesses

This helps users identify areas where business opportunities may be higher.

#### Bar Charts

**Top Categories**
- Ranks industries based on their **average opportunity score**
- Helps identify industries with stronger market potential.

**Top Cities**
- Ranks cities based on their **average opportunity score**
- Helps identify cities with better business opportunities.

#### Opportunity vs Competition Scatter Plot

- **X-axis:** Competition Score  
- **Y-axis:** Opportunity Score  

The chart is divided into four quadrants using average values:

- **Top-left:** High opportunity, low competition → Good market for new businesses
- **Top-right:** High opportunity, high competition → Strong but competitive market
- **Bottom-left:** Low opportunity, low competition → Weak market
- **Bottom-right:** Low opportunity, high competition → Saturated market

# How to use the Review Volatility:
   ## Filters:
1. Regions: Select the density region (rural, suburban, urban) you wish to analyze.
2. Business Categories: Choose between which of the top 10 most frequent business categories in a state you wish to visualize.
3. Metrics: Choose which metric you wish to compare states with using a color gradient.

   ## Charts:
1. Map: Hover over a state to see the metrics for that state and click on it to see that states volatility chart.
   
2. Line Chart: Divided into bins based on the number of reviews and graphed the top 10 categories per state based on their volatility dictated by the number of reviews. This chart changes based on the state that is selected, showing the volatility trends for that state.   

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





























