# 🌍 Global Insurance Analytics Dashboard

[![Power BI](https://img.shields.io/badge/Built%20with-Power%20BI-F2C811?style=flat-square&logo=powerbi)](https://powerbi.microsoft.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![Dataset](https://img.shields.io/badge/Dataset-Google%20Drive-34A853?style=flat-square)](https://drive.google.com/drive/folders/1aut4O2py6NOnN6pdEVUYpMiaB0_KMer7)
[![Status](https://img.shields.io/badge/Status-Complete-2d6a4f?style=flat-square)]()

---

## 📌 Overview

An interactive **Power BI dashboard** that benchmarks the global insurance landscape
across 180+ countries using two integrated datasets. Enables data-driven decisions
for international market expansion by visualising life insurance share, market share,
penetration, reinsurance ratio, and retention ratio — segmented dynamically by year,
category, and income group.

> **Dataset →** [Google Drive](https://drive.google.com/drive/folders/1aut4O2py6NOnN6pdEVUYpMiaB0_KMer7)

---

## 🎯 Objectives

- Compare key insurance metrics across 180+ countries globally
- Enable dynamic year and category-based analysis via Power BI parameters
- Visualise year-over-year growth with KPI cards and directional indicators
- Segment countries by World Bank income group on an interactive map
- Support data-driven decisions for global insurance market expansion

---

## 📂 Datasets

| Dataset | Type | Description |
|---|---|---|
| **Insurance Sample Dataset** | Primary | Insurance metrics per country per year |
| **Global Financial Development DB** | Secondary | World Bank income classification |

📥 **Download:** [Google Drive](https://drive.google.com/drive/folders/1aut4O2py6NOnN6pdEVUYpMiaB0_KMer7)

---

## 📊 Key Variables

| Variable | Description | Source |
|---|---|---|
| `Life Insurance Share` | Life premiums as % of total premiums | Primary |
| `Market Share` | Country share in global premium volume | Primary |
| `Penetration` | Total premiums as % of GDP | Primary |
| `Reinsurance Ratio` | Risk ceded to reinsurers | Primary |
| `Retention Ratio` | Risk retained by insurer | Primary |
| `Income Group` | World Bank income classification | Secondary |
| `Growth %` | YoY change (DAX calculated measure) | Derived |

---

## 🛠️ Methodology

### 1. 🗺️ Geographic Map
- Map visual coloured by **Income Group** from secondary dataset
- Income Group slicer synced across all visuals

### 2. 📋 KPI Table with Parameters
```dax
Year Parameter = GENERATESERIES(2010, 2022, 1)

Growth % =
  VAR Curr  = [Selected Category Value]
  VAR Prior = CALCULATE([Selected Category Value],
                SAMEPERIODLASTYEAR('Date'[Date]))
  RETURN IF(ISBLANK(Prior) || Prior=0, BLANK(),
            DIVIDE(Curr-Prior, Prior))
```

### 3. 🔺 Growth Indicator Shapes
```dax
Growth Indicator =
  IF([Growth %] > 0, "▲ Positive",
  IF([Growth %] < 0, "▼ Negative", "— No Change"))
```

### 4. 📈 Trend Line
- Line chart of selected category over time
- Triangle marker at last data point for directional emphasis

### 5. 🔽 Dashboard Filter
- Income Group slicer applied globally across all visuals

### 6. 🎨 Formatting
```dax
Dashboard Title =
  "Insurance Analytics — "
  & SELECTEDVALUE('Category List'[Category], "All")
  & " | FY " & FORMAT([Selected Year], "0")
```

---

## 📸 Screenshots

### Data Flow Architecture
![Data Flow](screenshots/insurance_flow_diagram.png)

### KPI Summary & Bar Chart
![KPI Chart](screenshots/insurance_kpi_bar_chart.png)

### Geographic Map
![Map View](screenshots/map_view.png)

### KPI Table with Growth Indicators
![KPI Table](screenshots/kpi_table.png)

### Trend Line
![Trend Line](screenshots/trend_line.png)

### Full Dashboard
![Full Dashboard](screenshots/full_dashboard.png)

---

## ⚙️ Tools & Techniques

| Tool / Technique | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard development & publishing |
| **DAX** | Growth %, dynamic titles, KPI measures |
| **Power Query (M)** | Data cleaning & transformation |
| **Data Modelling** | Country-key relationship between datasets |
| **What-If Parameters** | Year & Category dynamic selection |
| **Conditional Formatting** | Growth indicator shapes & colours |
| **Map Visual** | Geographic income-group colour encoding |
| **Line Chart** | Trend line with custom last-point marker |

---

## 💡 Key Insights

- **High-income dominance:** North America & Europe hold ~60% of global market share
- **Emerging market momentum:** Asia-Pacific records steepest YoY penetration growth
- **Retention vs reinsurance inverse:** Mature markets retain more risk domestically
- **Penetration tracks GDP:** High GDP per capita correlates with high penetration
- **Life insurance gap:** Life share in low-income markets stays below 20%

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
│   ├── insurance_flow_diagram.png          # Data flow architecture
│   ├── insurance_kpi_bar_chart.png         # KPI summary bar chart
│   ├── map_view.png                        # Geographic map visual
│   ├── kpi_table.png                       # KPI table with growth
│   ├── trend_line.png                      # Trend line visual
│   └── full_dashboard.png                  # Full dashboard overview
│
├── 📁 docs/
│   ├── data_dictionary.md                  # Variable definitions
│   └── dax_measures.md                     # All DAX code documented
│
└── README.md                               # Project documentation
```

---

## 🔗 How to Use

1. **Clone the repo**
   ```bash
   git clone https://github.com/your-username/insurance-dashboard.git
   cd insurance-dashboard
   ```
2. Download datasets from [Google Drive](https://drive.google.com/drive/folders/1aut4O2py6NOnN6pdEVUYpMiaB0_KMer7) → place in `/data`
3. Open `Insurance_Dashboard.pbix` in Power BI Desktop
4. Refresh data sources — update file paths in Power Query if needed
5. Use **Year** & **Category** slicers to explore metrics
6. Apply **Income Group** filter for segmented country analysis

---

## ✅ Conclusion

This Power BI dashboard provides a comprehensive, interactive platform for comparing
the global insurance landscape across income groups, regions, and years. By integrating
two datasets and exposing five key metrics through dynamic parameters, it transforms
raw data into clear, actionable intelligence for global expansion strategy.

---

## 👤 Author

**[Your Name]**
📧 your.email@example.com
🔗 [LinkedIn](https://linkedin.com/in/yourprofile) · [GitHub](https://github.com/your-username)

---
*Built with Power BI · DAX · Power Query*
*Data: Insurance Sample Dataset · World Bank Global Financial Development DB*
