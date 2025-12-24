# Feature Engineering Plan
Supporting: Problem Statement 01 – Blind Promotion Trap

## Objective
Translate business insights into predictive features
for baseline and promotional modeling.

---

## 1. Time-Based Features
- Day of week
- Week of year
- Month
- Holiday indicators

---

## 2. Lag & Rolling Features
- Lagged demand (7, 14, 28 days)
- Rolling mean / std
- Rolling baseline demand

---

## 3. Promotion Features
- promo_flag
- discount_pct
- promo_intensity (discount × duration)
- promo_frequency (rolling)

---

## 4. Price Features
- effective_price
- relative_price_change
- price index vs historical median

---

## 5. Inventory Features
- stock_on_hand
- days_of_cover
- stockout_risk_flag

---

## Output
Feature matrix for:
- Baseline model
- Promo uplift model
