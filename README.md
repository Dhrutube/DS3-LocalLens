# 🔍 Local Lens: Google Reviews Analytics

**Local Lens** is a data engineering and analytics project designed to transform raw Google Reviews data into actionable business intelligence. By processing large-scale datasets, we aim to recommend business expansion locations based on market density and sentiment, while helping customers identify the best businesses through statistical normalization.

The final product is an interactive Tableau dashboard that gives customers and businesses a new lens through which to search for their next meal or decide where to locate across two different cities.

---

## Accessing the Dashboard

👉 **Live Tableau Dashboard:**  
https://public.tableau.com/shared/XMMQ7FD7R?:display_count=n&:origin=viz_share_link

---
## Data Collection

This project uses multiple datasets from external sources.

### Google Local Data – McAuley Lab (UC San Diego)

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

### United States Cities Database

Source:  
https://simplemaps.com/data/us-cities

This dataset provides geographic information about U.S. cities, including:

- city name  
- latitude and longitude  
- population statistics  

It was used to match businesses to the **closest city location** using geographic coordinates.


### Google Business Categories Dataset

Source:  
https://www.lobstr.io/blog/google-business-categories

This dataset provides a structured list of Google Business categories and was used to group complex Google categories into **broader standardized categories** for analysis.

---

## Data Processing and Feature Engineering

* **Processing:** Includes sentiment analysis via **VADER**, feature engineering (Chain vs. Independent), and **Z-Score** normalization.
* **Storage:** Flattened CSV files managed via GitHub for version-controlled, BI-ready exports.
(add more)

---

### Sentiment Analysis (TF-IDF)

#### 1. Review Segmentation

Reviews were grouped based on:

- Area type: Urban, Suburban, Rural
- Business type: Restaurant vs. Non-Restaurant
- Sentiment group: Positive reviews vs. Negative reviews (based on star ratings)

This segmentation allowed us to compare how customer priorities differ across geographic and business contexts.

#### 2. Text Processing

- Extracted bigrams (two-word phrases) to capture more meaningful expressions such as “fast service” or “friendly staff”
- We used TF-IDF (Term Frequency–Inverse Document Frequency) to identify phrases that were important within each review group.

#### 3. Extracting Key Themes

For each segment (e.g., Urban Restaurants – Positive Reviews), we computed the top 20 bigrams with the highest TF-IDF scores.

These phrases represent themes that frequently appear in that segment's reviews while remaining distinctive compared to other reviews.

Examples of extracted phrases include:

- fast service  
- friendly staff  
- slow service  
These phrases were then compiled into a dataset used for visualization in Tableau.

---

## Tableau Dashboard
The final Tableau dashboard provides multiple analytical perspectives on the dataset.

---
### The Customer Lens

#### Overview
The **Customer Lens** focuses on understanding customer behavior and satisfaction across different businesses and locations.
This view allows users to explore how customers interact with businesses based on reviews, ratings, and geographic distribution.

---
#### Map Visualization
The map displays businesses geographically using latitude and longitude coordinates.

Each point represents a business.

- **Color:** Selected competition or relative score metric
- **Size:** Number of reviews

Larger circles indicate businesses that receive more customer reviews.

This helps identify areas with **high customer engagement and varying competition levels**.

---

#### Filters

Users can interact with the dashboard using:

- **Choose Category** – analyze specific industries
- **Choose City** – focus on specific local markets
- **Choose State** – explore regional trends

---
#### Metric Selector

Users can switch between several metrics:

- **Niche Competition Score**
- **Broad Competition Score**
- **Overall Category Relative Score**
- **Overall City Relative Score**

This allows exploration of different perspectives on competition and demand.

---

### The Business Lens

#### Overview
The **Business Lens** focuses on identifying potential market opportunities for businesses across locations and industries.
It helps evaluate where new businesses may have stronger opportunities based on **opportunity scores and competition levels**.

---

#### Map Visualization

The map shows the geographic distribution of businesses across selected states.

- **Color:** Average opportunity score
- **Size:** Concentration of businesses

This highlights regions where **market opportunities may be stronger**.

---

#### Filters

- **State** – filter by geographic region
- **City** – focus on local markets
- **Broad Category** – analyze specific industries

---

#### Opportunity vs Competition Scatter Plot

The scatter plot compares **opportunity scores and competition levels**.

- **X-axis:** Competition Score  
- **Y-axis:** Opportunity Score  

The chart is divided into four quadrants based on average values.

#### Quadrant Interpretation

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

### Sentiment Analysis Lens

#### Overview

The **Sentiment Lens** analyzes the language used in customer reviews to uncover common themes in positive and negative feedback.

This helps identify the factors that influence customer satisfaction and dissatisfaction.

---

#### Map of States

The map displays the states included in the review dataset.

Selecting a state allows users to analyze sentiment patterns for that region.

---

#### Top Positive Bigrams

This chart shows the most common phrases appearing in **positive reviews**
These phrases highlight aspects of businesses that customers value the most.

---

#### Top Negative Bigrams

This chart shows phrases frequently appearing in **negative reviews**
These phrases reveal common issues customers encounter.

---

#### Filters

Users can analyze sentiment using:

##### Area Type

- Urban  
- Suburban  
- Rural  

##### Business Type

- Restaurant  
- Non-Restaurant  

These filters allow comparisons of customer feedback across different environments and industries.

---

### Review Volatility

The **Review Volatility dashboard** explores how review patterns vary across states, business categories, and geographic regions.

---

#### Filters

Users can explore volatility using:

- **Regions** – Rural, Suburban, Urban  
- **Business Categories** – Top categories within each state  
- **Metrics** – Selected comparison metric  

---

#### Charts

##### Map
Hover over a state to see summary metrics and click to update the volatility chart.

##### Line Chart

Businesses are grouped into **bins based on number of reviews**, and the top categories per state are displayed based on volatility.
This visualization helps identify categories with **stable vs highly variable customer feedback**.

---
## Limitations
### Sentiment Analysis
Several limitations should be considered when interpreting this analysis:
  * Some reviews contain ratings without written text, reducing available language data.
  * Reviews are predominantly in English, which may underrepresent experiences from multilingual communities.
  * TF-IDF highlights frequent phrases, but it does not capture deeper context or sarcasm.
For these reasons, the analysis should be interpreted as directional insights into customer themes rather than a definitive sentiment score.

## 📂 Repository Structure
```plaintext


├── data/
│   ├── raw (metadata and reviews datasets)/            # Original, untouched data
│   └── processed (https://drive.google.com/drive/folders/1qB_tD36dqhy8q3UVVJqxr3pASNrUNSBu)/      
# Cleaned data ready
├── notebooks/          # .ipynb files for EDA and Tableau
│   ├──Brands_and_Reviews_Analysis/            # Analysis of Branding and Reviews Raw Datasets
│   ├──Generalized_Reviews_Analysis/            # Generalized Analysis of Reviews Raw Datasets
│   ├──Normalizing_Review_Culture/            # Score notebook for Tableau
│   ├──Volatility_analysis_refined/            # Volatility Analysis
│   └── rural_vs_suburban_vs_urban_refined/      # Region analysis and classification

├── outputs/            # Exported charts and PDF reports
│   └── Tableau Combined Dashboard/      # Combined Processed Data Into A Dashboard
├── README.md           # Project entry point
└── DESIGN_DOC.md       # This document
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
### Demographic and Economic Data Integration
Future work could enhance the opportunity analysis by incorporating demographic and economic indicators, such as:

- Population density
- Median household income
- Tourism activity
- Foot traffic estimates
Combining these variables with existing competition and sentiment metrics would allow the model to better estimate market demand and improve the accuracy of business opportunity predictions.
---

## Citation:
1. Li, J. (n.d.). Google Local review data. https://mcauleylab.ucsd.edu/public_datasets/gdrive/googlelocal/

2. The complete Google Business Categories list [Updated 2025]. (2024, November 6). https://www.lobstr.io/blog/google-business-categories

## Roadmap & Progress
* [x] **Phase 1-3:** Setup, Initial EDA, and Goal Definition.
* [/] **Phase 4-6:** Data Cleaning, Feature Engineering (Z-Scores), and Dashboard Prototyping.
* [ ] **Phase 8-10:** Finalizing sentiment word counts, loading state-wide data (TX, CA, NY), and Dino Cage Presentation.

---
















































