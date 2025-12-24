# Data Preprocessing Guidelines
Supporting: Problem Statement 01 – Blind Promotion Trap

## Objective
Deliver clean, leakage-free data suitable for causal and time-series modeling
of promotional effectiveness.

---

## 1. Promotion Label Integrity
- Validate promo_flag accuracy
- Remove overlapping or misaligned promotion periods
- Ensure promotion dates align with sales dates

---

## 2. True Baseline Identification
Define baseline observations as:

true_baseline = (promo_flag == 0) AND (stock_out_flag == 0)

These records are mandatory for baseline demand modeling.

---

## 3. Effective Price Feature
Create:

effective_price = list_price × (1 − discount_pct)

This feature is required for elasticity estimation.

---

## 4. Stock-Out Handling
- Mark stockout periods explicitly
- Do NOT impute demand during stockouts
- Zero-sales during stockout ≠ zero demand

---

## 5. Leakage Prevention
Ensure:
- No future promotions used in past data
- No future inventory signals in training
- Promo windows do not contaminate baseline windows

---

## 6. Deliverables
- cleaned_sales_data.csv
- feature_definitions.md
- baseline_mask_column
