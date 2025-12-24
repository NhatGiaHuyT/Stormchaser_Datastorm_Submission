# Modeling Plan: Promotion Effect Estimation
Supporting: Problem Statement 01 – Blind Promotion Trap

## Objective
Estimate causal promotional lift, profitability,
and generate actionable promotion decisions.

---

## 1. Baseline Demand Modeling
Purpose: Estimate counterfactual demand without promotion.

Methods:
- Moving averages
- Prophet (no promo regressors)
- XGBoost with time features

Output:
- Baseline demand prediction

---

## 2. Promotional Effect Modeling

### A. Causal Impact
Compare promo periods vs synthetic control.

### B. Double Machine Learning (EconML)
Separates:
- Promotion effect
- Price effect
- Seasonality
- External drivers

### C. Time-Series with Regressors
Models:
- ARIMAX
- XGBoost / LightGBM

Regressors:
- promo_flag
- discount_pct
- channel
- country
- time features

---

## 3. Outputs
- Baseline units
- Promo units
- Incremental lift
- Elasticity estimate
- Incremental margin

---

## 4. Decision Rules
Promotions allowed only if:
- Incremental margin > 0
- Stock_on_hand > expected lift
- Elasticity > 1
- Channel responsiveness is high
- Promo_rate below threshold

---

## Final Outcome
A promotion recommendation engine that maximizes
profit, stabilizes supply chain, and improves forecast accuracy.
