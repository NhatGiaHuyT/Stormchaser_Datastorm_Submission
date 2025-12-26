# Exploratory Data Analysis Guidelines  
Supporting: Problem Statement 02 – The Supply Chain Disconnect

## Objective
Identify supply-side instability, lead time uncertainty,
and inventory risk drivers that cause stockouts
despite accurate demand forecasting.

---

## 1. Lead Time Variability Analysis
Analyze:
- Distribution of `lead_time_days`
- Mean vs standard deviation of lead time
- Rolling lead time trends over time

Segment by:
- supplier_id
- country / city
- category / SKU

Flag:
- High variance suppliers
- Sudden lead time spikes

---

## 2. Supplier Reliability Assessment
Calculate per supplier:
- Average lead time
- Lead time standard deviation
- On-time delivery proxy (lead_time within expected range)

Classify suppliers into:
- Reliable
- Slow but stable
- Unreliable
- High-risk

Identify:
- Top contributors to lead time volatility
- Geographic patterns in supplier performance

---

## 3. Inventory Stability Analysis
Analyze:
- Distribution of `stock_on_hand`
- Stock volatility over time
- Stock trends before and after replenishment

Segment by:
- SKU
- Supplier
- City / country

Flag:
- High fluctuation SKUs
- Inventory oscillation patterns

---

## 4. Stockout Root Cause Analysis
Analyze:
- Frequency of `stock_out_flag`
- Stockouts during stable demand periods
- Stockouts vs lead time spikes

Cross-analyze:
- Units_sold vs stock_out_flag
- lead_time_days vs stock_out_flag
- Supplier reliability vs stockout frequency

Identify:
- Supply-driven stockouts
- Demand-independent stock failures

---

## 5. Demand vs Supply Mismatch
Analyze:
- Stable demand SKUs with high stockout rates
- Forecast accuracy proxy vs availability
- Stockouts during non-promotional periods

Goal:
- Separate demand error from supply failure
- Quantify supply-side risk exposure

---

## 6. Safety Stock Adequacy Check
Calculate:
- Average daily demand per SKU
- Lead time standard deviation
- Implied safety stock levels

Compare:
- Existing stock buffers vs required safety stock
- High service-level SKUs with insufficient buffers

Flag:
- Under-protected SKUs
- High uncertainty suppliers lacking inventory buffers

---

## 7. Geographic Risk Patterns
Analyze:
- Lead time variance by country and city
- Stockout concentration by region
- Supplier-region dependency risk

Identify:
- Regional bottlenecks
- High-risk supply corridors

---

## Deliverables
- Supply chain EDA notebook
- Supplier risk segmentation table
- Lead time volatility dashboard
- Inventory risk heatmap
- Actionable insights for planning and procurement teams
