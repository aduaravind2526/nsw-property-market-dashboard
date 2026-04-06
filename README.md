# 🏠 NSW Property Market Dashboard (2020–2025)

A Power BI dashboard analysing the New South Wales residential property market across rental and sales sectors, sourced from the NSW Department of Communities and Justice (DCJ).

Built as a portfolio project to demonstrate end-to-end data analytics skills — from raw government data through ETL, semantic modelling, and interactive visualisation.

---

## 📊 Dashboard Pages

### 1. NSW Rental Property Snapshot
Provides an overview of the rental market for any selected geography and period.

**Key Metrics (KPI Cards):**
- Median Weekly Rent
- YoY Median Rent Change %
- QoQ Median Rent Change %
- New Rental Bonds (selected period)
- Total Rentals (selected period)

**Visuals:**
- **Trend Chart** — Median rent by quarter for the selected year
- **IQR Distribution Chart** — IQR1, Median, and IQR3 rent values, answering: *Is rent growth broad-based or concentrated at the upper/lower end of the market?*

**Slicers / Filters:**
- Postcode (text input)
- LGA (dropdown)
- Dwelling Type: Flat/Unit, Townhouse, House, Other
- Number of Bedrooms
- Year

---

### 2. NSW Sales Property Snapshot
Provides an overview of the property sales market.

**Key Metrics (KPI Cards):**
- Median Sale Price
- YoY Median Sale Price Change %
- QoQ Median Sale Price Change %
- Total Properties Sold (selected period)

**Visuals:**
- **Trend Chart** — Median sale price by quarter and year
- **IQR Distribution Chart** — IQR1, Median, and IQR3 for sale price

**Slicers / Filters:**
- Postcode (text input)
- LGA (dropdown)
- Dwelling Type: Strata, Non-Strata
- Year

---

### 3. Affordability Analysis
Combines rental and sales data to support rent-vs-buy decision making.

**Key Metrics (KPI Cards):**
- Median Annual Rent
- Median Sale Price
- Gross Rental Yield (%)
- Price-to-Rent Ratio (PTR)
- Total Rental Bonds

**Visuals:**
- **Affordability Matrix (Scatter Plot)** — PTR on X-axis, Gross Rental Yield on Y-axis. Quadrants indicate:
  - *Top-left*: Strong Buy
  - *Bottom-left*: Okay Buy
  - *Bottom-right*: Rent over Buy
  - Tooltips surface Annual Rent, Sale Price, Yield, and PTR on hover
- **Top 10 LGAs by Price-to-Rent Ratio**
- **Top 10 LGAs by Gross Rental Yield**

**Slicers / Filters:**
- Postcode (text input)
- LGA (dropdown)
- Year

---

## 🔧 Technical Overview

### Data Sources
- **NSW Department of Communities and Justice (DCJ)** — [Previous Rent and Sales Reports](https://dcj.nsw.gov.au/about-us/families-and-communities-statistics/housing-rent-and-sales/previous-rent-and-sales-reports.html)
- Data covers quarterly periods from **2020 Q1 to 2025 Q2**
- Granularity: Postcode × Year × Quarter × Dwelling Type × Bedroom Count

### ETL — Power Query
- Imported quarterly rental and sales files by postcode
- Standardised data types and column formats across rental and sales datasets
- Merged a **Postcode-to-LGA lookup table** to enable LGA-level filtering and aggregation
- Applied data cleansing: null handling, type enforcement, consistent category naming

### Semantic Model — Power BI
- Star schema with fact tables for Rentals and Sales, dimension tables for Geography (Postcode/LGA), Time, and Dwelling Type
- Key calculated measures (DAX):
  - `Median Weekly Rent`, `Median Sale Price`
  - `YoY Change %` and `QoQ Change %` (time-intelligence)
  - `Gross Rental Yield = Median Annual Rent / Median Sale Price`
  - `Price-to-Rent Ratio = Median Sale Price / Median Annual Rent`
  - `IQR1` and `IQR3` using `PERCENTILEINC`

---

## 🚀 Upcoming Features

- **Mortgage Sensitivity Analysis** — Model repayments across varying interest rates and LVRs
- **Income Contribution Breakdown** — Proportion of household income allocated to rent or mortgage by LGA

---

## 👤 About

Built by **Aditya Aravind** — Data Reporting Analyst | Business & IT Student (Finance & Business Information Systems)

Connecting data, finance, and storytelling to build actionable insights.

🔗 [LinkedIn](https://www.linkedin.com/in/aditya-aravind-432156176/) | 📧 Reach out via LinkedIn

---

## 📄 Data Licence

Source data is publicly available from the NSW Department of Communities and Justice. This project is for educational and portfolio purposes only.
