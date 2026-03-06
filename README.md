# Google Reviews Project

Project Overview

Local Lens is a data engineering and analytics project designed to transform raw Google Reviews data into actionable business intelligence. By processing large-scale datasets, we aim to:
Optimize Business Location: Recommend where companies should expand based on market density and sentiment.
Enhance Customer Choice: Help users identify the best businesses by reevaluating ratings through statistical normalization.


Data Infrastructure & Pipeline

The project handles 5GB+ JSON files using a decentralized processing model to prevent memory crashes.
Ingestion: Utilizes custom parse() generators to stream data without loading the entire metadata object.
Processing: Sentiment analysis via VADER, feature engineering (Chain vs. Independent), and Z-Score normalization.
Storage: Flattened CSV files managed via Git LFS or GitHub for version-controlled, BI-ready exports.
Presentation: Exploratory analysis in Plotly and executive-facing dashboards in Tableau. 


Technical Stack

 Category           Tool               Implementation Detail
Development        VS Code      Primary environment for Python/Jupyter scripts.
Analysis           Python       Pandas, NumPy, NLTK (VADER) for sentiment.
Visualization      Plotly       Interactive EDA and trend identification.
BI Reporting       Tableau      Final interactive dashboards and maps.
Version Control    GitHub       Managing code and data versioning.


Data Schema

We merge two primary datasets to generate our insights:
Review Data: Includes user_id, rating, text, and gmap_id.
Metadata: Includes business name, category, latitude/longitude, and price.


Roadmap & Progress

[x] Phase 1-3: Setup, Initial EDA, and Goal Definition.
[/] Phase 4-6: Data Cleaning, Feature Engineering (Z-Scores), and Dashboard Prototyping.
[ ] Phase 8-10: Finalizing sentiment word counts, loading state-wide data (TX, CA, NY), and Dino Cage Presentation.


Directory Structure

Plaintext
├── data/
│   ├── raw/            # Original, untouched data [cite: 63]
│   └── processed/      # Cleaned data ready for BI [cite: 64]
├── notebooks/          # .ipynb files for EDA and Plotly [cite: 65]
├── src/                # .py scripts for data pipelines [cite: 66]
├── outputs/            # Exported charts and PDF reports [cite: 67]
└── README.md           # This document [cite: 68]


The Team:
Aiden Hernandez
Karsten Lowe
Aurora Cong
Ngo Nguyen Anh Tran
Project Lead: Dhruv Sehgal
