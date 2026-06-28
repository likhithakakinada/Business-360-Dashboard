### 
🔗 [Live Dashboard Link](https://app.powerbi.com/view?r=eyJrIjoiNTNkZjRjYTItZTVjZi00NDlkLTg3NTYtOGQwMDI5N2I2YzczIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9&pageName=416c4537e3be0dec766b)
---


## 🧩 Problem Statement

**AtliQ Hardware** is a fast-growing global electronics company that was making critical business decisions based on intuition, surveys, and spreadsheets. After suffering significant losses in the Latin American market — decisions made without data — the leadership team recognized the urgent need for a centralized analytics platform.

**The challenges:**
- ❌ No unified view of financial performance across regions and segments
- ❌ Poor forecast accuracy causing excess inventory and stockout losses
- ❌ Inability to identify underperforming customers, products, and markets
- ❌ No executive-level consolidated view for strategic decision-making
- ❌ Benchmark comparison was manual and inconsistent

---

## 💡 Solution — Business Insights 360

A fully interactive, multi-page Power BI platform delivering a 360° view of business performance across **Finance, Sales, Marketing, Supply Chain, and Executive** functions.

**What it solves:**
- ✅ Real-time P&L visibility with benchmark and target comparison
- ✅ Forecast accuracy tracking with risk classification (EI / OOS)
- ✅ Customer and product profitability analysis
- ✅ Market share trends vs competitors
- ✅ Executive-level strategic snapshot with sub-zone insights

---

## 🛠 Tech Stack

| Technology | Purpose |
|------------|---------|
| Power BI Desktop | Dashboard development, visuals, and design |
| Power Query (M) | ETL — data cleaning and transformation |
| DAX | All KPI measures, calculated columns, conditional logic |
| MySQL | Source database — actuals and forecast data |
| Excel / CSV | Supporting data — targets, operational expenses, market share |
| Bookmarks & Buttons | Interactive overlay panels, toggle states, navigation |

---

## 📊 Dashboard Pages — What Each Page Does

### 💰 Finance View
Profit and Loss analysis with dynamic benchmark comparison.
- Net Sales, GM%, Net Error% KPI cards with BM sub-labels
- Full P&L statement matrix — from Gross Sales to Net Profit
- Net Sales area chart — monthly trend vs benchmark
- Top/Bottom breakdown by Region and Segment
- Dynamic BM warning message when benchmark is unavailable
- Toggle between vs Last Year and vs Target

### 🤝 Sales View
Customer and product commercial performance.
- Customer Performance table with GM% conditional formatting
- Product Performance table by segment
- Net Sales vs GM% scatter chart with Target Gap Tolerance slicer
- Unit Economics — revenue composition and margin breakdown donuts
- Hover tooltip showing NS & GM% trend per customer

### 📣 Marketing View
Product profitability and market performance analysis.
- Product Performance with Net Profit columns
- Performance Matrix — scatter chart with bookmark toggle (GM% / NP%)
- Region/Market/Customer Performance table
- Unit Economics — donut + waterfall (Gross Margin → OpEx → Net Profit)

### 🚚 Supply Chain View
Forecast accuracy and inventory risk management.
- Custom KPI strip: Forecast Accuracy%, Net Error, Absolute Error
- Accuracy/Net Error Trend — combo chart (bars + dual-line overlay)
- Key Metrics by Customer — full risk classification (EI / OOS)
- Key Metrics by Product — segment-level forecast performance

### 👔 Executive View
C-suite consolidated strategic dashboard.
- 4 KPI cards — Net Sales, GM%, Net Error%, Forecast Accuracy%
- Key Insights by Sub Zone — with conditional formatting icons
- Revenue by Division and Revenue by Channel — donut charts
- PC Market Share Trend — stacked area chart vs 4 competitors
- Yearly Trend — combo chart across NS$, GM%, NP%, Market Share%
- Top 5 Customers and Top 5 Products by Revenue

---

## 🗄 Data Architecture

Built on a **Star Schema** data model optimized for analytical performance.

### Fact Tables
```
fact_actuals_estimates     — Sales actuals and estimates
fact_forecast_monthly      — Monthly forecast data
```

### Dimension Tables
```
dim_customer               — Customer master data
dim_product                — Product catalog
dim_market                 — Market and region hierarchy
dim_date                   — Date table (fiscal year Sep–Aug)
```

### Supporting Tables
```
freight_cost               — Logistics cost data
manufacturing_cost         — Production cost data
operational_expense        — OpEx by market and year
marketshare                — Competitor market share data
NsGmTarget                 — Sales and margin targets
```

### Semantic Layer
```
Key Measures               — All DAX measures (50+ measures)
```

---

## 🧮 Key DAX Measures

```dax
-- Net Sales with dynamic period comparison
Net Sales = SUM(fact_actuals_estimates[net_sales_amount])

-- Gross Margin Percentage
GM % = DIVIDE([Gross Margin], [Net Sales], 0)

-- Forecast Accuracy
Forecast Accuracy % = 
1 - DIVIDE([Absolute Error], [Forecast Quantity], 0)

-- Dynamic BM Warning Message
BM Message = 
VAR _ns_bm = [NS $ BM]
RETURN
IF(ISBLANK(_ns_bm), 
   "BM Target/s is not available for the selected filters", 
   "")

-- Net Profit Percentage
Net Profit % = DIVIDE([Net Profit], [Net Sales], 0)
```

---

## 📈 Key Business Insights Uncovered

- 📌 **Net Profit is -14.65%** — the business is loss-making at net level driven by high operational expenses
- 📌 **APAC drives 53% of Net Sales** but carries the highest absolute loss
- 📌 **AtliQ's PC Market Share grew from ~2% (2018) to ~5.9% (2022)** — strong competitive momentum
- 📌 **Forecast Accuracy at 68.12%** — 1 in 3 forecasts is wrong, driving EI/OOS inventory risk
- 📌 **AtliQ Exclusive has the highest GM% at 45.80%** among top customers — most profitable relationship
- 📌 **Notebook segment** is the highest revenue contributor at $2.96bn but Net Profit% is -14.73%
- 📌 **Latin America (LATAM)** has the smallest revenue share at 0.3% — significant growth opportunity or exit candidate

---


## 📚 What I Learned

**Technical skills built:**
- Advanced DAX — CALCULATE, SWITCH, DIVIDE, VAR, time intelligence
- Star schema data modeling with 10+ tables
- Power Query transformations and M language
- Bookmark-driven interactivity and overlay UI patterns
- Custom theme JSON development
- Performance optimization — disabled auto date/time, measure variables

**Business domain knowledge:**
- P&L structure from Gross Sales to Net Profit
- Supply chain KPIs — Forecast Accuracy, Net Error, EI vs OOS
- Market share analysis and competitive benchmarking
- Financial variance analysis — Actual vs Benchmark vs Target

---
