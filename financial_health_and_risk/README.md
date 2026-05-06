# 📊 Financial Health and Risk Assessment (Power BI)

## 📌 Project Overview

This Power BI project analyzes company financial health, bankruptcy risk, and operational performance using structured datasets.

The dashboard provides **interactive insights into risk segmentation, profitability, churn behavior, and financial ratios**.

---

## 📊 Dashboard Preview

<img width="1078" height="756" alt="financial health and risk" src="https://github.com/user-attachments/assets/d61c8778-601f-41d4-9539-c4eec73fc758" />


*Overview of financial risk, profitability, and company segmentation*

---

## 🎯 Objectives

* Identify **high-risk companies**
* Analyze **bankruptcy patterns**
* Compare **financial ratios across segments**
* Evaluate **profitability impact on risk**
* Deliver a **business-ready interactive dashboard**

---

## 🗂️ Project Structure

```id="x7k2md"
📁 Data/   → CSV datasets  
📁 viz/    → Power BI files (.pbix), data model, dashboard images  
```

---

## 🧮 Data Model

The project uses multiple aggregated tables:

* `risk_segmentation`
* `portfolio_summary`
* `warning_indicators`
* `time_based_trends`
* `KPI`

  <img width="1280" height="820" alt="model" src="https://github.com/user-attachments/assets/e47e0260-027c-441d-8bc7-9e510fcaca61" />


Tables are used independently for visualization due to pre-aggregated structure.

---

## 🧮 Calculated Measures (DAX)

The following DAX measures were created to enhance analysis:

### Core Metrics

```DAX id="q9i8m2"
Total Companies = SUM(KPI[company_count])

Total Bankruptcies = SUM(KPI[bankrupt_count])

Bankruptcy Rate % =
DIVIDE([Total Bankruptcies], [Total Companies])
```

---

### Financial Ratios (Adjusted)

```DAX id="u6c2jd"
Avg Current Ratio = AVERAGE(risk_segmentation[avg_current_ratio])

Avg Quick Ratio = AVERAGE(risk_segmentation[avg_quick_ratio])

Avg Debt Ratio = AVERAGE(risk_segmentation[avg_debt_ratio])
```

---

### Risk Classification

```DAX id="z8b1qp"
Risk Level =
IF([Bankruptcy Rate %] > 0.05, "High Risk", "Low Risk")
```

---

## 📈 Dashboard Features

* 📊 Risk segmentation by indicator type
* 📉 Bankruptcy rate comparison
* 📦 Company distribution analysis
* 📊 Financial ratio comparison
* 🔍 Scatter plot (Debt vs ROA)
* 📈 Profitability vs bankruptcy relationship

---

## 🧠 Key Insights

* Bankruptcy risk is **not evenly distributed** across company segments
* Companies with **moderate profitability show unexpectedly high risk**
* Liquidity ratios alone do **not guarantee financial stability**
* Debt ratio has **limited predictive power** in isolation
* Risk patterns suggest **multi-factor analysis is required**

---

## 💡 Conclusion

The dashboard demonstrates that traditional financial indicators are insufficient to fully explain bankruptcy risk.

A more advanced approach combining multiple factors is required for accurate financial risk assessment.

---

## 🚀 Tools & Technologies

* Power BI
* DAX (Data Analysis Expressions)
* Data Modeling
* Data Visualization

---

## 📎 Files Included

* `.pbix` file (interactive dashboard)
* Data model structure
* Dashboard screenshots

---

## 👤 Author

**Dmitruz Ruzhytskyi**
Data Analyst / Software Developer

---
