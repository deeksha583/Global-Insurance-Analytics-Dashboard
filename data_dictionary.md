# Data Dictionary — Insurance Analytics Dashboard

## Primary Dataset: `insurance_sample_dataset.xlsx`

| Variable | Data Type | Description | Example |
|---|---|---|---|
| `Country` | Text | Country name (join key) | United States |
| `Year` | Integer | Year of record | 2022 |
| `LifeInsuranceShare` | Decimal (%) | Life premiums as % of total insurance premiums | 38.4 |
| `MarketShare` | Decimal (%) | Country's share in global insurance premium volume | 6.7 |
| `Penetration` | Decimal (%) | Total insurance premiums as % of GDP | 4.2 |
| `ReinsuranceRatio` | Decimal (%) | Proportion of risk ceded to reinsurers | 21.5 |
| `RetentionRatio` | Decimal (%) | Proportion of risk retained by primary insurer | 78.5 |

---

## Secondary Dataset: `global_financial_development.xlsx`

| Variable | Data Type | Description | Example |
|---|---|---|---|
| `Country` | Text | Country name (join key to primary) | United States |
| `CountryCode` | Text | ISO 3-letter country code | USA |
| `Region` | Text | World Bank geographic region | North America |
| `IncomeGroup` | Text | World Bank income classification | High income |
| `Year` | Integer | Year of classification | 2022 |

---

## Derived / Calculated Variables (DAX)

| Variable | Type | Formula Summary |
|---|---|---|
| `Growth %` | Measure | (Current Year Value − Prior Year Value) / Prior Year Value |
| `Growth Indicator` | Measure | ▲ Positive / — No Change / ▼ Negative based on Growth % |
| `Selected Category Value` | Measure | Dynamic value based on Category Parameter selection |
| `Dashboard Title` | Measure | Concatenated string of selected category + selected year |
| `KPI Color` | Measure | Hex colour string based on Growth % sign |

---

## Income Group Classification (World Bank)

| Group | GNI per Capita (USD) |
|---|---|
| Low income | ≤ $1,135 |
| Lower-middle income | $1,136 – $4,465 |
| Upper-middle income | $4,466 – $13,845 |
| High income | > $13,845 |

---

## Data Relationship

```
insurance_sample_dataset[Country]  ──►  global_financial_development[Country]
         (Many)                                      (One)
```
Join type: **Many-to-One** on `Country` column.
Relationship direction: **Single** (primary → secondary).
