# Modeling Plan  
Supporting: Problem Statement 02 – The Supply Chain Disconnect

## Objective
Design analytical and modeling approaches to identify,
quantify, and mitigate supply-side instability—particularly
lead time volatility—that causes stockouts despite
accurate demand forecasting.

This plan focuses on supplier reliability, safety stock
optimization, and early risk detection.

---

## 1. Problem Decomposition

The supply chain failure is driven by:
- High variability in `lead_time_days`
- Unreliable supplier performance
- Inadequate safety stock buffers
- Weak coordination between demand planning and procurement

Modeling must therefore go beyond demand forecasting
and explicitly quantify **supply uncertainty**.

---

## 2. Modeling Scope & Targets

### 2.1 Primary Targets
- `lead_time_days` (regression / probabilistic modeling)
- `stock_out_flag` (classification / risk prediction)

### 2.2 Secondary Metrics
- Service level (fill rate proxy)
- Supplier reliability score
- Inventory risk index

---

## 3. Feature Groups

### 3.1 Supplier Features
- supplier_id
- lead_time_days (lags, rolling mean, rolling std)
- historical delay frequency
- supplier-region interaction

### 3.2 Demand & Inventory Features
- units_sold (rolling mean, volatility)
- stock_on_hand
- stock_out_flag (lagged)
- lead_time_days × demand interaction

### 3.3 Temporal & External Features
- weekday / month / seasonality
- holiday indicators
- weather (temperature, rain_mm)
- regional effects (country, city)

---

## 4. Modeling Strategy

### 4.1 Lead Time Forecasting
Purpose: Quantify uncertainty, not just point estimates.

Methods:
- Rolling average baselines
- Quantile regression (P50 / P90 lead times)
- Gradient Boosting Regressors (LightGBM / XGBoost)
- Bayesian or probabilistic models (optional)

Outputs:
- Expected lead time
- Lead time uncertainty bands

---

### 4.2 Supplier Reliability Segmentation
Purpose: Classify suppliers by risk profile.

Methods:
- Aggregated lead time statistics
- K-Means or Hierarchical Clustering
- Rule-based thresholds

Segments:
- Reliable
- Slow but stable
- Unstable
- High-risk

---

### 4.3 Stockout Risk Prediction
Purpose: Predict stockout probability before it occurs.

Target:
- `stock_out_flag`

Methods:
- Logistic Regression (baseline)
- XGBoost / LightGBM Classifier
- Imbalanced learning techniques

Key Predictors:
- Predicted lead time
- Stock-on-hand vs expected demand
- Supplier reliability class

Outputs:
- Stockout probability
- Risk ranking by SKU / location

---

## 5. Safety Stock Optimization

### 5.1 Safety Stock Formula
Use dynamic safety stock calculation:

SS = Z × σ_LT × √D

Where:
- σ_LT = standard deviation of lead time
- D = average daily demand
- Z = service level factor

### 5.2 Dynamic Adjustment Logic
- Increase SS for high-variance suppliers
- Reduce SS for stable suppliers
- Apply higher service levels to A-class SKUs

---

## 6. Simulation & Stress Testing

### 6.1 Monte Carlo Simulation
Simulate:
- Lead time distributions
- Demand variability
- Replenishment cycles

Outputs:
- Stockout probability distribution
- Inventory buffer sufficiency

### 6.2 Scenario Analysis
Test:
- Supplier delay shocks
- Demand surges
- Lead time improvement initiatives

---

## 7. Model Evaluation

### 7.1 Lead Time Models
Metrics:
- MAE
- RMSE
- Coverage of prediction intervals

### 7.2 Stockout Models
Metrics:
- ROC-AUC
- Precision / Recall
- Recall on stockout class (critical)

Business validation:
- Reduction in stockout frequency
- Improved service levels

---

## 8. Decision Support Outputs

Deliverables:
- Supplier risk scorecard
- Dynamic safety stock recommendations
- Stockout early-warning alerts
- Replenishment prioritization lists

These outputs integrate directly into
S&OP and procurement workflows.

---

## 9. Deployment & Governance

- Weekly model refresh
- Supplier performance monitoring
- Exception-based alerts
- Continuous improvement loop with suppliers

---

## Conclusion
Demand forecasting accuracy alone cannot guarantee
product availability.

By explicitly modeling lead time uncertainty,
supplier reliability, and inventory risk,
this framework aligns demand planning with
supply execution—closing the disconnect and
protecting service levels.
