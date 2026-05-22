# Global-Insurance-Analytics-Dashboard
An interactive analytics dashboard designed to track, visualize, and analyze global insurance data. Features real-time KPI monitoring, policy distribution insights, claims trends, and risk assessment metrics to drive data-driven decision-making.

## 📌 Overview

An interactive Power BI dashboard designed to analyze and compare the global insurance landscape across countries. This project integrates two datasets — the **Insurance Sample Dataset** and the **Global Financial Development Database** — to deliver dynamic, data-driven insights for strategic global expansion.

---
## 🎯 Objectives

- Compare key insurance metrics across countries on a global scale
- Enable dynamic year and category-based analysis via parameters
- Visualize growth trends with KPIs and directional indicators
- Support executive decision-making for global market entry and expansion
- Provide income-group filtering for segmented market analysis

---
## 📂 Datasets

| Dataset | Description |
|---|---|
| **Insurance Sample Dataset** | Primary — insurance metrics by country and year |
| **Global Financial Development Database** | Secondary — income classification per country |



> Both datasets are integrated using Power BI's data modeling and relationship features.

---## 📊 Key Variables

| Variable | Description |
|---|---|
| `Life Insurance Share` | % of life insurance in total premiums |
| `Market Share` | Country's share in global insurance market |
| `Penetration` | Insurance premiums as % of GDP |
| `Reinsurance Ratio` | Proportion of risk ceded to reinsurers |
| `Retention Ratio` | Risk retained by the primary insurer |
| `Income Group` | Country's income classification (World Bank) |
| `Growth %` | Year-over-year change in selected category |

---

## 🛠️ Methodology

### 1. 🗺️ Geographic Map
- Power BI map visual showing countries
- Color encoding based on **Income Group** (from secondary dataset)
- Interactive **Income Group filter** applied across all visuals

### 2. 📋 KPI Table
- Two dynamic parameters created:
  - **Year Selection** — choose analysis year
  - **Category Selection** — choose metric (Life Insurance Share, Market Share, Penetration, Reinsurance Ratio, Retention Ratio)
- Calculated **Growth %** measure (DAX)
- Table with **dynamic title** driven by selected category

### 3. 📈 Growth Indicator Shapes
- Conditional formatting applied to Growth %
- Three states displayed with visual shapes:
  - 🔺 **Positive** — growth above 0
  - ⬛ **No Change** — growth equals 0
  - 🔻 **Negative** — growth below 0

### 4. 📉 Trend Line
- Line chart for selected category over time
- Visual emphasis using **arrows/triangles** at the last data point
- Dynamically updates based on parameter selection

### 5. 🔽 Dashboard Filter
- Income Group slicer applied globally across all visuals
- Synchronized filtering for consistent, comparable views

### 6. 🎨 Formatting
- Consistent color scheme, fonts, and layout
- Professional dark/light theme for polished presentation
- Dynamic titles and tooltips for enhanced UX

---

## ⚙️ Tools & Techniques

| Tool / Technique | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard development and publishing |
| **DAX (Data Analysis Expressions)** | Growth % measures, calculated columns |
| **Power Query (M Language)** | Data transformation and cleaning |
| **Data Modeling** | Relationship mapping between datasets |
| **Conditional Formatting** | Growth indicator shape logic |
| **Power BI Parameters** | Year and category dynamic selection |
| **Map Visual** | Geographic income distribution |
| **Line Chart** | Trend visualization with custom markers |

---

## 💡 Key Insights

- Countries in **High Income** groups lead in Market Share and Penetration rates
- **Life Insurance Share** varies significantly between developing and developed markets
- **Reinsurance Ratio** inversely correlates with market maturity in several regions
- Year-over-year **Growth %** highlights emerging markets with rapid insurance expansion
- The **Retention Ratio** reveals risk appetite differences across income brackets

---

## 🗂️ Project Structure

```
insurance-dashboard/
│
├── 📁 data/
│   ├── insurance_sample_dataset.xlsx       # Primary dataset
│   └── global_financial_development.xlsx   # Secondary dataset
│
├── 📁 dashboard/
│   └── Insurance_Dashboard.pbix            # Main Power BI file
│
├── 📁 screenshots/
│   ├── map_view.png                        # Geographic map visual
│   ├── kpi_table.png                       # KPI table with growth
│   ├── trend_line.png                      # Trend line visual
│   └── full_dashboard.png                  # Full dashboard overview
│
├── 📁 docs/
│   └── data_dictionary.md                  # Variable definitions
│
└── README.md                               # Project documentation
```

---

## ✅ Conclusion

This Power BI dashboard empowers insurance executives and analysts with a comprehensive, interactive tool for global market analysis. By integrating income classification data with key insurance metrics and enabling dynamic filtering and year-over-year comparison, the dashboard supports confident, data-backed decisions for international expansion strategy.

---

