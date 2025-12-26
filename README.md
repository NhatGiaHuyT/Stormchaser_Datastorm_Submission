# 📦 FMCG Demand & Supply Chain Analytics  
**Promotion Effectiveness & Supply Chain Risk Modeling**

---

## 📌 Project Summary

This repository presents a **business-driven analytics solution** for two critical FMCG challenges:

1. **Blind Promotion Trap** – Promotions executed without understanding true demand impact  
2. **Supply Chain Disconnect** – Stockouts caused by supplier lead time instability despite accurate demand forecasts  

The project demonstrates how **advanced analytics, causal thinking, and risk-based modeling** can be used to improve profitability, service levels, and supply chain stability.

---

## 🎯 Business Objectives

- Optimize promotion strategy using **incremental lift and elasticity**
- Prevent margin erosion caused by over-promotion
- Detect supply chain fragility early
- Reduce stockouts through **supplier risk modeling**
- Improve collaboration between demand planning and supply chain teams

---

## 🧩 Problem Statements

### **Problem 01 – Blind Promotion Trap**
Promotions are applied broadly without evaluating:
- Baseline demand
- Incremental sales
- Price sensitivity
- Inventory readiness
- Profitability

This leads to:
- Artificial demand spikes
- Margin destruction
- Forecast distortion
- Unnecessary supply chain stress

📌 **Goal:** Identify when promotions create real value vs. when they waste margin.

---

### **Problem 02 – Supply Chain Disconnect**
Even with stable demand forecasts:
- Lead times are volatile
- Safety stock is underestimated
- Stockouts still occur

📌 **Goal:** Model supplier uncertainty and predict stockout risk proactively.

---

## 📁 Repository Structure
```bash
├── docs/
│ ├── problem_statement_01_blind_promotion.md
│ ├── data_preprocessing_guidelines.md
│ ├── eda_guidelines.md
│ ├── feature_engineering_plan.md
│ ├── modeling_plan.md
│ │
│ ├── problem_statement_02_supply_chain_disconnect.md
│ ├── eda_supply_chain_disconnect.md
│ ├── feature_engineering_plan_supply_chain_disconnect.md
│ └── modeling_plan_supply_chain_disconnect.md
│
├── notebooks/
│ ├── 01_promotion_effect_model.ipynb
│ └── 02_supply_chain_disconnect.ipynb
│
├── requirements.txt
└── README.md
```


---

## 📓 Notebooks Overview

### **01_promotion_effect_model.ipynb**
**Focus:**
- Baseline demand estimation
- Incremental lift calculation
- Price elasticity analysis
- Promotion ROI evaluation

**Outputs:**
- Over-promotion detection
- SKU-level promotion recommendations
- Channel-specific promo effectiveness

---

### **02_supply_chain_disconnect.ipynb**
**Focus:**
- Supplier lead time uncertainty modeling
- Stockout risk prediction
- Dynamic safety stock logic
- Early warning system

**Outputs:**
- Supplier risk rankings
- Stockout probability scores
- Actionable inventory alerts

---

## 🧠 Analytics & Modeling Philosophy

- Business-first modeling (not metric-driven)
- Separation of demand and supply uncertainty
- Risk-based decision making
- Time-aware validation (no leakage)
- Interpretability for operations teams

---

## 📈 Business Impact

This solution enables organizations to:

- Reduce wasteful discounting
- Increase promotional ROI
- Prevent stockouts before they happen
- Stabilize supply chain operations
- Improve service levels on high-value SKUs
- Align Demand Planning and S&OP processes

---

## ⚙️ Setup & Installation

Clone the repository and install dependencies:

```bash
git clone <https://github.com/keniondang/Stormchaser_Datastorm_Submission>
cd <Stormchaser_Datastorm_Submission>
pip install -r requirements.txt
