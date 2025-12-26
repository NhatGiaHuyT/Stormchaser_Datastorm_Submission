# Feature Engineering Plan  
Supporting: Problem Statement 02 – The Supply Chain Disconnect

## Objective
Design robust, leakage-safe features that transform raw
operational data into predictive signals capturing:

- Lead time uncertainty
- Supplier reliability
- Inventory instability
- Demand–supply mismatch

The goal is to enable proactive stockout prevention and
data-driven safety stock optimization.

---

## 1. Design Principles
Feature engineering will:
- Use only historical information (no future leakage)
- Emphasize volatility and risk, not raw values
- Aggregate at operationally meaningful levels
- Be interpretable for supply chain decision-making

---

## 2. Lead Time Features
**Purpose:** Quantify delay risk and uncertainty.

Create rolling features per supplier / SKU / location:
- Rolling mean lead time (7d, 14d, 30d)
- Rolling standard deviation of lead time
- Lead time coefficient of variation (CV)
- Week-over-week lead time change

Derived indicators:
- lead_time_risk_score
- lead_time_spike_flag

---

## 3. Supplier Reliability Features
**Purpose:** Capture execution consistency.

Aggregate by `supplier_id`:
- Average lead time
- Lead time variance
- Delay frequency (% of days above historical P75)
- Contribution to stockouts

Derived features:
- supplier_reliability_index
- supplier_risk_class (encoded)

Supplier-level features are joined back to SKU-store data.

---

## 4. Inventory Dynamics Features
**Purpose:** Detect buffer instability.

Create:
- stock_on_hand rolling mean
- stock_on_hand rolling standard deviation
- Stock cover days = stock_on_hand / avg_daily_demand
- Inventory volatility index

Risk flags:
- low_stock_flag
- high_inventory_variability_flag

---

## 5. Demand Stability Features
**Purpose:** Separate demand-driven from supply-driven risk.

Create:
- Rolling mean of units_sold (7d, 14d, 30d)
- Demand volatility (rolling std)
- Demand trend slope
- Stable demand indicator

These features help identify supply failures when demand is stable.

---

## 6. Demand–Supply Interaction Features
**Purpose:** Model operational risk directly.

Create:
- expected_demand_during_LT
- stock_gap = stock_on_hand − expected_demand_during_LT
- demand × lead_time interaction
- reorder_risk_index

These features are critical for stockout prediction models.

---

## 7. Safety Stock Features
**Purpose:** Enable dynamic inventory buffers.

Compute:
- σ_LT = lead time standard deviation
- σ_D = demand standard deviation
- Required safety stock per service level

Derived features:
- required_safety_stock
- safety_stock_gap
- under_buffered_flag

---

## 8. Temporal & Seasonality Features
**Purpose:** Capture operational stress periods.

Enhance time features:
- End-of-month flag
- Peak season indicator
- Holiday proximity windows
- Supplier capacity stress periods

---

## 9. Geographic Risk Features
**Purpose:** Capture network fragility.

Create:
- Lead time variance by city / country
- Regional stockout frequency
- Supplier–region dependency score

Supports regional sourcing and risk mitigation strategies.

---

## 10. Feature Validation & Selection
Apply:
- Correlation filtering
- Feature importance analysis (tree-based models)
- Stability testing over time

Exclude:
- Features with future leakage
- Highly collinear aggregates
- Non-actionable indicators

---

## Deliverables
- Feature engineering notebook
- Feature dictionary
- Supplier risk feature table
- Inventory risk indicators
- Model-ready datasets

---

## Outcome
This feature engineering framework converts raw
transactional data into **decision-grade signals** that
enable:
- Early stockout detection
- Supplier risk management
- Dynamic safety stock policies
- Strong alignment between demand planning and supply execution
