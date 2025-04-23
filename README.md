# 🌾 Analyzing the Impact of Climate Change Expectations on Food Prices in Nigeria

This project explores how local perceptions of climate extremes—such as droughts and floods—affect food price trends across Nigerian communities. Combining **Excel**, **Power BI**, and **Python (Google Colab)**, this analysis provides an integrated view of data processing, visualization, and model insights.

---

## 🎯 Objectives

- Investigate how communities expect climate change to evolve.
- Analyze food price variations across regions in Nigeria.
- Identify gender and economic sector trends related to climate perceptions.
- Combine descriptive and predictive insights using multiple tools.

---

## 📁 Tools & Workflow

| Tool        | Purpose                                  |
|-------------|------------------------------------------|
| Excel       | Data cleaning, filtering, and pre-processing |
| Power BI    | Interactive dashboards & summary visuals |
| Google Colab| Data merging, analysis, modeling (Python) |

---

## 📦 Data Sources

- **GHS-Panel Wave 5 (2023/2024)**:
  - Section 6b: Expectations on Climate Extremes
  - Section 8: Food Prices
  - Household & Labour Sections for demographics and sector data

---

## 📊 Project Structure

```bash
climate-food-prices-nigeria/
│
├── 📂 data/                # Excel and CSV datasets
│   ├── climate_section6b.xlsx
│   ├── food_prices_section8.xlsx
│   └── merged_dataset.csv
│
├── 📂 notebooks/           # Google Colab notebooks (Python analysis)
│   └── 01_Climate_Food_Analysis.ipynb
│
├── 📂 reports/             # Power BI dashboards (.pbix) and screenshots
│   └── food-climate-dashboard.pbix
│
├── 📂 visuals/             # Exported charts and images
│   └── price_trend_by_state.png
│
├── README.md              # Project overview
└── requirements.txt       # Python packages for Colab
