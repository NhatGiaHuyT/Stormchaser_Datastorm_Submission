# Exploratory Data Analysis Guidelines
Supporting: Problem Statement 01 – Blind Promotion Trap

## Objective
Identify promotional inefficiencies, elasticity behavior,
and inventory readiness using structured analysis.

---

## 1. Baseline vs Promotion Performance
Analyze:
- Average units_sold (promo vs non-promo)
- Lift % by SKU / country / channel
- SKUs with high volume but low lift

---

## 2. Promotion Penetration
Calculate per SKU:

promo_rate = sum(promo_flag) / total_days

Flag:
- High promo_rate
- High baseline demand
→ Over-promotion risk

---

## 3. Price Elasticity Analysis
- Plot effective_price vs units_sold
- Estimate elasticity per SKU / channel
- Segment elastic vs inelastic products

---

## 4. Inventory Readiness
Analyze:
- stock_on_hand before promotion
- stock_out_flag during promotion
- Lost sales due to inventory constraints

---

## 5. Margin Impact
Calculate:
- Incremental units
- Incremental margin
- Negative ROI promotions

---

## Deliverables
- EDA notebook
- Key insight summary
- Feature recommendations
