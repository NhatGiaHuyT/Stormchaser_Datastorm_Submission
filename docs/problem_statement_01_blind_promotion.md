# Problem Statement 01: The “Blind Promotion” Trap in FMCG Demand Planning

## Executive Summary
This problem statement investigates inefficiencies in current FMCG promotional strategies,
where promotions are executed without understanding baseline demand, price elasticity,
inventory readiness, or profitability.

Using 3 years of daily FMCG sales data (1.1M rows), we identify over-promotion,
margin erosion, and supply chain instability caused by blind discounting.
The objective is to redesign promotions using data-driven, causal, and inventory-aware analytics.

---

## 1. Introduction
Promotions are a key lever in FMCG to drive volume, protect market share,
and stimulate customer demand. However, when promotions are applied
without analytical evaluation, they can generate artificial demand,
destroy margins, and destabilize the supply chain.

This problem statement diagnoses promotional inefficiencies
and defines the analytical direction to fix them.

---

## 2. Problem Statement: The Blind Promotion Trap
Current promotions are executed without evaluating:
- Whether the SKU needs a promotion
- Whether inventory can support uplift
- Whether the promotion is profitable
- Whether customers are price-sensitive
- Whether baseline demand is already strong

This leads to wasteful discounting and unreliable demand signals.

---

## 3. Theoretical Background

### 3.1 Baseline Demand
Baseline demand is the expected demand without promotions and without stockouts:

Dbaseline = E[units_sold | promo_flag = 0, stock_out_flag = 0]

Baseline demand is the benchmark for measuring true promotional impact.

---

### 3.2 Incremental Lift
Promotions must be evaluated on incremental sales:

Lift = Dpromo − Dbaseline

High total sales during promotion do not imply effectiveness if baseline demand is already high.

---

### 3.3 Price Elasticity
Elasticity measures customer response to price changes:

Elasticity = %ΔQuantity / %ΔPrice

- Elasticity > 1 → Promotions effective
- Elasticity < 1 → Promotions wasteful

Many FMCG SKUs exhibit low elasticity.

---

### 3.4 Promotional Bias & Cannibalization
Promotions introduce:
- Artificial demand spikes
- Pre-promo loading
- Post-promo dips

These distort true demand and corrupt forecasts.

---

### 3.5 Supply Chain Impact
Promotions trigger sudden demand surges.
If inventory is unprepared, stockouts occur,
causing lost sales and bullwhip effects upstream.

---

## 4. Evidence Observed in Dataset
Key symptoms identified:
- High baseline demand SKUs still promoted
- Discounts increase gross sales but reduce margins
- Stockouts during promotions
- Uniform promotions across low-response regions

---

## 10. Conclusion
The FMCG promotion strategy suffers from over-promotion,
margin erosion, and inventory stress.
A data-driven, causal, and inventory-aware approach
is required to restore profitability and forecast stability.

This problem statement defines the business diagnosis.
Execution is defined in the supporting documents.
