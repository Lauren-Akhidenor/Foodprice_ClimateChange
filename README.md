# 🌾 Analyzing the Impact of Climate Change Expectations on Food Prices in Nigeria

This project explores how local perceptions of climate extremes such as droughts and floods affect food price trends across Nigerian communities. Combining **Excel**, **Power BI**, and **Python (Google Colab)**, this analysis provides an integrated view of data processing, visualization, and model insights.

---

## 🎯 Objectives

- Generate clear, Excel-style bar chart visualizations using Pytho
- Investigate how communities expect climate change to evolve.
- Analyze food price variations across regions in Nigeria.
- Combine descriptive and predictive insights using multiple tools.

---

## 📁 Tools & Workflow

| Tool        | Purpose                                  |
|-------------|------------------------------------------|
| Excel       | Data cleaning, merging of data, filtering, and pre-processing |
| Power BI    | Interactive dashboards & summary visuals |
| Google Colab| Analysis, modeling & predicting (Python) |

---

## 📦 Data Sources

- **GHS-Panel Wave 5 post harvest community (2023/2024)** :
  - Section 6b: Expectations on Climate Extremes
  - Section 8: Food Prices
  

---

## 📊 Project Structure

```bash
climate-food-prices-nigeria/
│
├── 📂 data/                # Excel datasets
│   ├── Expectation_of_climate_section6b.xlsx
│   ├── food_prices_section8.xlsx
│   └── merged_dataset.xlsx
│
├── 📂 notebooks/           # Google Colab notebooks (Python analysis)
│   └── 🌾 Analyzing the Impact of Climate Change Expectations on Food Prices in Nigeria.ipynb
│
├── 📂 reports/             # Power BI dashboards (.pbix) and screenshots
│   └── food-climate-dashboard.pbix


--------------
## 📈 Analyses Performed:

### 🔹 Excel:

cleaned the dataset

Power Query execution

Merged Food price and Expectation of climate change dataset together










### 🔹 Power Bi:










### 🔹 Python (Google Colab):


### 🔹 1. Sector-wise Climate Expectation Count
- Counted number of respondents expecting future climate shocks by sector
- Plotted bar chart showing which economic sector had more people expecting climate change

### 🔹 2. Food Price Comparison by Climate Expectation & State
- Compared average food prices (`c2q3`) between states
- Grouped by `climate_exp_cd` (0 = No, 1 = Yes) to check price impact
- Plotted bar chart showing how prices vary based on climate perception

### 🔹 3. Predictive Modeling: Climate Expectation → Food Price
- Used Linear Regression to predict food prices based on:
  - `climate_exp_cd` (climate expectation)
  - `sector`
- Generated R-squared value, coefficients for interpretation
- Insight: See how climate expectations numerically influence food price trends

### ✅ Data Integrity
- Values like 0/1 for climate expectations and sector were left as-is
- No label encoding or renaming was applied, keeping raw data structure clean
