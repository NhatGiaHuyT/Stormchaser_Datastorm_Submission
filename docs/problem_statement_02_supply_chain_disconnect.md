# The Supply Chain Disconnect  
## Lead Time Volatility & Stockout Risk in FMCG

---

## 1. Problem Statement

Accurate demand forecasting alone does not guarantee product availability.

In the current FMCG operating environment, **lead time volatility** — rather than demand uncertainty — is a primary driver of stockouts. Even when demand is stable and well forecasted, unpredictable replenishment lead times prevent inventory from arriving on time.

This exposes a critical **disconnect between demand planning and supply chain execution**.

> **Key Insight**  
> Stockouts are often caused by supply uncertainty, not forecast error.

---

## 2. Business Impact

Lead time instability creates significant operational, financial, and strategic damage.

### Operational Impact
- Frequent stockouts (`stock_out_flag = 1`)
- High volatility in `stock_on_hand`
- Emergency replenishment and expediting
- Planning instability for downstream operations

### Financial Impact
- Lost sales due to unavailability
- Higher procurement and logistics costs
- Inventory imbalance (simultaneous overstock and stockout)

### Strategic Impact
- Declining service levels
- Reduced customer trust
- Disproportionate impact on high-value A-class SKUs

---

## 3. Data Evidence

Analysis of the FMCG dataset reveals clear supply-side instability:

- `lead_time_days` shows **high variance** (σ ≈ 2 days)
- Stockouts occur even when demand is stable
- `stock_on_hand` fluctuates widely
- Supplier performance (`supplier_id`) is inconsistent
- Lead time behavior varies significantly by city and country

These patterns confirm that stockouts are driven primarily by **supply uncertainty**, not demand volatility.

---

## 4. Why Forecasting Alone Cannot Solve This

Traditional planning implicitly assumes:
Demand Uncertainty >> Supply Uncertainty



However, real-world data shows:
Supply Uncertainty ≈ Demand Uncertainty



As a result:
- Accurate forecasts still lead to stockouts
- Safety stock based on average lead time is insufficient
- Planning decisions are structurally biased

Forecasting accuracy does not translate into service level reliability without supply-side modeling.

---

## 5. Solution Overview

Resolving the supply chain disconnect requires **explicit modeling of uncertainty** and **tight integration between demand and supply planning**.

The solution consists of four core pillars:

1. Supplier lead time modeling  
2. Dynamic safety stock calculation  
3. Sales & Operations Planning (S&OP) integration  
4. Early warning and risk detection system  

---

## 6. Solution Pillar 1 — Supplier Lead Time Modeling

### Objective
Move beyond average lead time and quantify **supplier reliability and risk**.

### Approach
For each supplier (segmented by city and country):

- Compute rolling mean lead time
- Compute rolling standard deviation of lead time
- Model probabilistic lead time distributions
- Simulate replenishment uncertainty using Monte Carlo methods

This captures both expected delay and variability.

---

### Supplier Reliability Segmentation

| Segment | Characteristics |
|-------|-----------------|
| Reliable | Low mean, low variance |
| Slow but stable | High mean, low variance |
| Unreliable | Low mean, high variance |
| High risk | High mean and high variance |

This segmentation enables **supplier-specific inventory and sourcing strategies**.

---

## 7. Solution Pillar 2 — Dynamic Safety Stock

### Why Static Safety Stock Fails

Static safety stock assumes stable lead times and uniform supplier behavior — assumptions that do not hold in practice.

---

### Dynamic Safety Stock Formula

\[
SS = Z \times \sigma_{LT} \times \sqrt{D}
\]

Where:
- **Z** = service level factor (e.g., 1.65 for 95%)
- **σₗₜ** = standard deviation of lead time
- **D** = average daily demand

---

### Business Interpretation

- Higher uncertainty suppliers require larger buffers
- Stable suppliers require less safety stock
- Critical SKUs receive targeted protection

This ensures inventory is allocated **where risk is highest**, not evenly across the network.

---

## 8. Solution Pillar 3 — S&OP Integration

### Problem
Demand planning and supply chain execution operate in silos.

### Resolution
Implement a structured **Sales & Operations Planning (S&OP)** process:

- Share demand forecasts with suppliers
- Conduct weekly capacity and lead time reviews
- Align promotion calendars with supply readiness
- Reconcile demand plans with supply constraints

---

### Shared KPIs Across Functions

| KPI | Purpose |
|----|--------|
| OTIF (On-Time-In-Full) | Supplier delivery reliability |
| Lead time variance | Supply risk indicator |
| Service level | Customer impact |
| Forecast adherence | Planning quality |

Shared KPIs enforce accountability and alignment.

---

## 9. Solution Pillar 4 — Early Warning System

### Objective
Detect supply risk **before stockouts occur**.

---

### Risk Triggers

Alerts are generated when:
- Lead time exceeds historical thresholds
- Supplier lead time variance increases
- Stock falls below reorder point
- Supplier reliability score deteriorates

---

### Business Outcome

- Proactive replenishment actions
- Reduced emergency procurement
- Improved service continuity
- Faster decision-making under uncertainty

---

## 10. Expected Outcomes

Implementing this framework delivers measurable improvements:

| Area | Expected Improvement |
|----|----------------------|
| Stockouts | Significant reduction |
| Inventory stability | Improved |
| Emergency costs | Reduced |
| Supplier accountability | Increased |
| Service level | Improved |
| Planning credibility | Restored |

---

## 11. Key Takeaway

> Demand forecasting predicts what customers want.  
> Supply chain analytics ensures the product arrives on time.

Stock availability depends on **understanding and managing uncertainty**, not eliminating it.

---

## 12. Relationship to Promotion Optimization

This supply chain framework complements promotion modeling by:

- Ensuring promotions are executed only when supply is reliable
- Preventing promotion-driven stockouts
- Improving forecast stability during campaigns

Together, demand and supply analytics create a **closed-loop planning system**.

---

## 13. Next Steps

- Integrate supplier reliability scores into replenishment policies
- Combine promotion lift forecasts with lead time risk
- Automate alerts and monitoring dashboards
- Extend modeling to multi-echelon inventory networks
