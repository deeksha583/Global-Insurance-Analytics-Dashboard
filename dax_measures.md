# DAX Measures — Insurance Dashboard

## 1. Year Parameter
```dax
Year Parameter = GENERATESERIES(2010, 2022, 1)
Selected Year  = SELECTEDVALUE('Year Parameter'[Year Parameter],
                   MAX('Date'[Year]))
```

## 2. Category Parameter
```dax
Category List = DATATABLE("Category", STRING,
  {{"Life Ins. Share"},{"Market Share"},
   {"Penetration"},{"Reinsurance Ratio"},{"Retention Ratio"}})
```

## 3. Selected Category Value
```dax
Selected Category Value =
  VAR Cat = SELECTEDVALUE('Category List'[Category])
  RETURN
    SWITCH(Cat,
      "Life Ins. Share",    AVERAGE(Insurance[LifeInsuranceShare]),
      "Market Share",       AVERAGE(Insurance[MarketShare]),
      "Penetration",        AVERAGE(Insurance[Penetration]),
      "Reinsurance Ratio",  AVERAGE(Insurance[ReinsuranceRatio]),
      "Retention Ratio",    AVERAGE(Insurance[RetentionRatio])
    )
```

## 4. Growth % Measure
```dax
Growth % =
  VAR Curr  = [Selected Category Value]
  VAR Prior = CALCULATE([Selected Category Value],
                SAMEPERIODLASTYEAR('Date'[Date]))
  RETURN
    IF(ISBLANK(Prior) || Prior = 0, BLANK(),
       DIVIDE(Curr - Prior, Prior))
```

## 5. Growth Indicator
```dax
Growth Indicator =
  IF([Growth %] > 0, "▲ Positive",
  IF([Growth %] < 0, "▼ Negative", "— No Change"))
```

## 6. Dynamic Dashboard Title
```dax
Dashboard Title =
  "Insurance Analytics — "
  & SELECTEDVALUE('Category List'[Category], "All Categories")
  & " | FY " & FORMAT([Selected Year], "0")
```

## 7. KPI Color (Conditional Formatting)
```dax
KPI Color =
  IF([Growth %] > 0, "#1D9E75",
  IF([Growth %] < 0, "#D85A30", "#888780"))
```

## 8. Map Income Color
```dax
Map Color =
  SWITCH(SELECTEDVALUE('Country'[IncomeGroup]),
    "High income",    "#1D9E75",
    "Upper middle",   "#378ADD",
    "Lower middle",   "#7F77DD",
    "Low income",     "#BA7517",
    "#CCCCCC"
  )
```
