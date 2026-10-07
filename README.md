# Real-World Retail Sales Data Analysis

An end-to-end practical retail sales data analytics project examining real-world transactional records from a major UK-based online retailer. This project evaluates commercial sales performance, customer ordering behavior, assortment dynamics, geographic market distribution, and temporal demand seasonality using descriptive and diagnostic analytics.

---

## Project Overview

In commercial retail operations, transaction logs represent the single most reliable source of operational truth. This project processes, audits, cleanses, and analyzes over 540,000 transaction records spanning December 1, 2010 through December 9, 2011.

Rather than applying black-box predictive algorithms or ungrounded machine learning models, this analysis adheres strictly to practical descriptive and diagnostic retail analytics. It translates granular line-item data into actionable business intelligence for executive decision-makers, inventory managers, and commercial strategy leads.

---

## Business Problem

Retail businesses face critical commercial questions:
- **Revenue Drivers:** Which specific products and categories generate the majority of enterprise revenue?
- **Seasonality & Capacity:** When do peak purchasing surges occur, and how severe is the operational strain ahead of the holiday season?
- **Customer Segmentation:** To what extent does the business depend on high-volume wholesale accounts versus individual consumers?
- **Market Expansion:** How concentrated is the domestic core market versus international export corridors?
- **Basket Dynamics:** How do order quantity, unit pricing, and catalog breadth interact to influence total transaction value?

Addressing these questions requires auditing and cleaning real-world transaction logs—eliminating cancellation credit notes, zero/negative pricing, and unassigned guest purchases—to establish a clean operational baseline.

---

## Dataset Information

- **Dataset Name:** Online Retail
- **Entity Type:** UK-based registered non-store online retail enterprise
- **Product Domain:** Unique all-occasion giftware, seasonal accessories, and home decor
- **Customer Base:** Hybrid consumer (B2C) and wholesale trade (B2B)
- **Timeframe:** December 1, 2010 to December 9, 2011 (374 calendar days)
- **Raw Dimensions:** 541,909 rows × 8 columns (22.62 MB)
- **Cleaned Dimensions:** 392,692 rows × 9 columns (36.29 MB)

### Schema Definition
| Field Name | Type | Description |
| :--- | :--- | :--- |
| `InvoiceNo` | Nominal / String | 6-digit integer uniquely identifying each transaction. Prefix 'C' indicates a cancellation. |
| `StockCode` | Nominal / String | 5-digit integer uniquely identifying each distinct product SKU. |
| `Description` | Nominal / String | Product title / description name. |
| `Quantity` | Integer | Quantity of each product per transaction line. |
| `InvoiceDate` | Datetime | Exact date and time when the transaction was generated. |
| `UnitPrice` | Float (GBP) | Product price per unit in sterling (£). |
| `CustomerID` | Nominal / Integer | 5-digit integer uniquely identifying each registered customer account. |
| `Country` | Nominal / String | Customer's country of residence / shipping destination. |
| `Revenue` *(Engineered)* | Float (GBP) | Calculated line gross revenue: `Quantity × UnitPrice`. |

---

## Dataset Source

- **Publisher:** UC Irvine Machine Learning Repository
- **Official Repository URI:** [https://archive.ics.uci.edu/dataset/352/online+retail](https://archive.ics.uci.edu/dataset/352/online+retail)
- **Citation:** Chen, D., Sain, S.L., & Guo, K. (2012). Data mining for the online retail industry: A case study of RFM model-based customer segmentation using data mining. *Journal of Database Marketing & Customer Strategy Management*, 19(3), 197-208.

---

## Technologies Used

- **Language:** Python 3.10+
- **Data Manipulation & Analysis:** Pandas, NumPy
- **Data Visualization:** Matplotlib, Seaborn
- **File Parsing & I/O:** OpenPyXL
- **Interactive Notebook Environment:** Jupyter Notebook / JupyterLab

---

## Project Structure

```
Retail-Sales-Data-Analysis/
├── data/
│   ├── raw/
│   │   └── Online Retail.xlsx         # Pristine raw source dataset (unmodified)
│   └── processed/
│       └── online_retail_cleaned.csv  # Validated cleaned transactional dataset
├── notebooks/
│   └── Retail_Sales_Analysis.ipynb    # Complete, fully executed analysis notebook
├── visualizations/
│   ├── 01_monthly_revenue.png         # Monthly revenue trend & seasonality (300 DPI)
│   ├── 02_top_10_products_revenue.png # Top 10 revenue-generating products (300 DPI)
│   ├── 03_top_10_countries_revenue.png# Global vs. international revenue share (300 DPI)
│   ├── 04_quantity_distribution.png   # Line quantity distribution & pack sizes (300 DPI)
│   ├── 05_revenue_distribution.png    # Line and order revenue distributions (300 DPI)
│   ├── 06_top_10_customers_revenue.png# Top 10 customer accounts by revenue (300 DPI)
│   ├── 07_quantity_vs_revenue.png     # Product volume vs. monetary yield (300 DPI)
│   └── 08_correlation_heatmap.png     # Order-level correlation matrix (300 DPI)
├── README.md                          # Project documentation
└── requirements.txt                   # Environment package dependencies
```

---

## Analysis Performed

The analysis is structured into 14 distinct, sequentially executed notebook sections:

1. **Section 1 — Project Introduction:** Retail domain context, enterprise background, dataset origin, and analytical scope.
2. **Section 2 — Load and Inspect Data:** Ingesting raw Excel files, auditing schema, profiling missing values, and characterizing initial anomalies.
3. **Section 3 — Data Cleaning:** Multi-stage filtering pipeline (omitting unassigned guest checkouts, removing cancellations prefixed with 'C', filtering non-positive quantities and unit prices, deduplicating records), engineering the `Revenue` attribute, and exporting the processed dataset while preserving raw data integrity.
4. **Section 4 — Sales Overview:** Calculating macro enterprise KPIs (total revenue, unit volume, order counts, unique customers, catalog SKU breadth, average and median order values).
5. **Section 5 — Monthly Sales Trend:** Longitudinal revenue tracking from Dec 2010 to Dec 2011, seasonal acceleration profiling, and partial-month run-rate analysis.
6. **Section 6 — Top Products:** Product-level revenue aggregation and Pareto distribution analysis.
7. **Section 7 — Top Countries:** Geographic concentration analysis across domestic UK and 36 international export markets.
8. **Section 8 — Quantity Analysis:** Parametric and non-parametric distribution profiling of order line units and pack-size clustering.
9. **Section 9 — Revenue Distribution:** Right-skewed ticket size modeling across line items and consolidated customer invoices.
10. **Section 10 — Customer Analysis:** Longitudinal spend aggregation, identifying top 10 accounts, and key account concentration assessment.
11. **Section 11 — Product Performance:** Log-log volume vs. revenue scatter analysis and product quadrant segmentation.
12. **Section 12 — Correlation Analysis:** Order-level Pearson and Spearman correlation matrices across revenue, quantity, price, and SKU breadth.
13. **Section 13 — Business Insights:** Practical, data-grounded commercial recommendations for inventory planning, logistics, CRM, and merchandising.
14. **Section 14 — Final Summary:** Concise bulleted synthesis of key findings.

---

## Key Findings

- **Total Realized Enterprise Revenue:** £8,887,208.89 across 392,692 validated transactions and 5,152,002 units sold.
- **Wholesale-Driven Profile:** Average Order Value (AOV) is **£479.56** (median: £303.45), with discrete order quantity spikes at multiples of 6 and 12, confirming wholesale buyers as the primary commercial engine.
- **Q4 Holiday Seasonality:** Monthly revenue remained steady around ~£580k/month from January to August 2011 before surging in September (£950.7k) and peaking in **November 2011 at £1,156,205.61** (+102% over summer baseline).
- **Product Assortment Concentration:** Top 10 products generated **£865,042.46 (9.73%)** of gross revenue, led by *Paper Craft Little Birdie* (£168.5k) and *Regency Cakestand 3 Tier* (£142.3k).
- **Domestic Footprint & European Corridors:** Domestic UK sales generate **81.97% (£7.29M)** of total revenue. Overseas sales (£1.60M) are concentrated in the Netherlands (£285.4k), Ireland (£265.3k), Germany (£228.7k), France (£208.9k), and Australia (£138.5k).
- **Key Account Dependency:** The top 10 customer accounts contribute **£1,455,475.25 (16.38%)** of all company sales. The top client (Customer 14646, Netherlands) generated £280,206.02 (3.15% of enterprise revenue).
- **Basket Diversity Drives Order Value:** A strong positive correlation ($r = 0.672$) between unique line items per invoice and total order value demonstrates that cross-category basket variety directly expands order revenue.

---

## Visualization List

Every visualization is formatted with clear labels, currency notations, and saved at **300 DPI**:

1. `01_monthly_revenue.png`: Bar-and-line chart of monthly revenue trajectories illustrating steady baseline operations and the Q4 holiday surge.
2. `02_top_10_products_revenue.png`: Horizontal bar chart of the 10 highest-earning product SKUs with monetary labels in thousands of pounds (£k).
3. `03_top_10_countries_revenue.png`: Two-panel visualization contrasting UK domestic market share (82.0%) against the top 10 international export markets.
4. `04_quantity_distribution.png`: Log-scale boxplot and focused frequency distribution highlighting discrete wholesale case-pack spikes at 6, 12, 24, and 36 units.
5. `05_revenue_distribution.png`: Dual log-scale histograms demonstrating positive skewness across line-item and invoice-level transaction values.
6. `06_top_10_customers_revenue.png`: Horizontal bar chart detailing top 10 customer lifetime values, international origin, and individual percentage shares.
7. `07_quantity_vs_revenue.png`: Log-log scatter plot of unit volume versus total revenue across all 3,665 catalog products, color-coded by average unit price.
8. `08_correlation_heatmap.png`: Annotated correlation matrix measuring linear relationships across order revenue, quantity, catalog variety, and pricing.

---

## How to Run the Notebook

### 1. Prerequisites
Ensure Python 3.10 or higher is installed on your system.

### 2. Install Dependencies
Navigate to the project root directory and install required dependencies:
```bash
cd "Retail-Sales-Data-Analysis"
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook
Launch the Jupyter server:
```bash
jupyter notebook notebooks/Retail_Sales_Analysis.ipynb
```
Or use JupyterLab:
```bash
jupyter lab
```

### 4. Execute the Notebook
Select **Kernel -> Restart & Run All** to execute all 47 cells sequentially. All tables will render inline and all 8 high-resolution charts will be generated in `visualizations/`.

---

## Educational & Project Disclaimer

This project was developed for educational and portfolio demonstration purposes as part of an applied data analytics internship. The data utilized is publicly available from the UCI Machine Learning Repository and represents historical anonymized retail transactions. All conclusions, analyses, and strategic suggestions are based solely on descriptive and diagnostic statistical evaluations of the provided dataset and do not represent internal proprietary disclosures from the original retail enterprise.
