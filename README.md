# Global-E-Commerce-Return-Refund-Intelligence-Multi-Market-Analysis

## Overview
This project is a multi-market data analytics case study examining return and refund behavior across three real-world e-commerce datasets. The analysis covers the complete data pipeline — from raw data ingestion and cleaning, through exploratory data analysis and advanced SQL querying, to an interactive 3-page Power BI executive dashboard.
Each market dataset answers a different business question:

UK (Online Retail II) — Which products, countries, and time periods drive the most returns and revenue loss?
Brazil (Olist) — Does delivery delay cause cancellations? Which categories and states perform worst?
Global Logistics — Which warehouses and shipment modes fail most, and what is the customer satisfaction impact?


## Key Highlights

Analyzed 500K+ UK transactions and identified return rate, revenue lost, and peak return timing
Merged 8 relational Olist tables into a master DataFrame and correlated delivery delay with 1-star reviews
Found that 1-star reviews in Brazil cluster around the highest delivery delay days
Identified the worst-performing warehouse and shipment mode from the logistics dataset
Wrote 15 advanced SQL queries covering CTEs, window functions, UNION ALL, CASE WHEN, and NULLIF
Built a 3-page interactive Power BI dashboard for executive-level stakeholder reporting


## Datasets
#DatasetSourceSizeMarket1Online Retail IIKaggle500K+ rowsUK2Brazilian E-Commerce — OlistKaggle100K+ orders, 8 tablesBrazil3E-Commerce Shipping DatasetKaggle11K rowsGlobal Logistics

## Tech Stack
CategoryToolsLanguagePython 3.10+Data ManipulationPandas, NumPyVisualizationMatplotlib, SeabornDatabaseSQLite via sqlite3DashboardPower BI DesktopEnvironmentGoogle Colab / Jupyter NotebookVersion ControlGit, GitHub

## Analysis Breakdown
UK Market — Return & Refund Analysis

Identified returns using invoice cancellation logic — Invoice starting with C or Quantity below zero
Engineered 9 feature columns: IsReturn, TotalValue, RefundAmount, YearMonth, DayOfWeek, Hour, and more
Analyzed monthly return trends, top returned products by frequency and refund value, country-wise analysis, and peak return timing by day and hour
Produced 4 publication-quality charts

Brazil Market — Cancellation & Delivery Analysis

Merged 8 relational Olist tables into one master DataFrame using Pandas
Engineered delivery delay feature: delivery_delay_days = delivered_date - estimated_date
Correlated delivery delays with customer review scores (1 to 5 scale)
Analyzed cancellation rates by product category, customer state, payment type, and order value segment
Produced 5 charts including monthly cancellation trend and state-level performance

Logistics — Shipping Performance Analysis

Analyzed late delivery rates across 5 warehouse blocks (A, B, C, D, F) and 3 shipment modes (Ship, Flight, Road)
Investigated product importance level vs delivery failure rate
Explored relationship between discount offered and late delivery behavior
Profiled high-risk shipments: late AND low-rating AND high care calls
Produced 5 charts


## SQL Analysis — 15 Queries
All queries are written in SQLite and fully documented with explanations in sql/sql_queries_explained.md
Concepts demonstrated:
ConceptQueries UsedCTE — WITH ... ASQ2, Q8, Q10, Q13, Q14Window Functions — RANK, DENSE_RANK, SUM OVER, COUNT OVERQ2, Q3, Q4, Q6, Q8, Q11, Q12, Q13PARTITION BYQ2CASE WHEN SegmentationQ1, Q5, Q7, Q10, Q13, Q14, Q15UNION ALL Cross-table StackingQ15NULLIF Safe DivisionQ9HAVING Group-level FilterQ4, Q8, Q9Conditional AggregationQ7Multi-column GROUP BYQ14Compound WHERE FilterQ7, Q14

## Key Business Findings
UK Market

Returns follow a seasonal pattern with spikes in Q4 post-holiday months
Top returned products often have vague or misleading descriptions — a product listing problem
United Kingdom dominates return volume; a few international markets show disproportionately high return rates relative to order volume
Specific days of the week show higher return concentration — useful for operations staffing

Brazil Market

Clear negative correlation between delivery delay and review score — 1-star reviews average significantly more delay days than 5-star reviews
Certain product categories exceed 10% cancellation rate consistently
High-value premium orders cancelled represent concentrated revenue risk despite lower cancellation frequency
States with highest cancellation rates also show the lowest average review scores

Global Logistics

One warehouse block records the highest late delivery rate — an immediate audit priority
High-importance products show no evidence of priority dispatch — a process gap
Customers who made 4 or more care calls consistently rate 1 to 2 stars — a first-call resolution problem
Larger discounts correlate with late delivery — potentially indicating reactive discounting after service failure

## How to Run
1. Clone the repository
bashgit clone https://github.com/mahasweta-talik/global-ecommerce-return-analysis.git
cd global-ecommerce-return-analysis
2. Install dependencies
bashpip install pandas numpy matplotlib seaborn openpyxl
3. Download datasets from Kaggle
Place all CSV and Excel files inside the data/ folder as listed in the project structure above.
4. Run the analysis notebook
Open notebooks/global_ecommerce_returns_analysis.py in Google Colab or Jupyter Notebook and run all cells from top to bottom.
5. Explore the SQL queries
