# Enterprise Dynamic Product Pricing Engine (Supervised Regression Pipeline)

An end-to-end cloud-native machine learning regression application engineered to predict continuous fluid target store values (Optimal Market Price) by modeling market competition dynamics, stock limitations, and demand impulses.

## Technical Architecture & PM Strategy Summary

### 1. Preprocessing & Outlier Mitigation Strategy
- **Core Concept:** Evaluated targeted retail warehouse data, identifying severe outlier skews within higher-tier luxury item inventories. 
- **Data Action:** Implemented **Logarithmic Transformation** ($\log(1+y)$) across target output variables to compress right-skewed revenue profiles, preventing baseline algorithmic bias on lower-to-mid tier stock items.
- **Feature Standardization:** Passed divergent numerical data ranges (`inventory_stock_level` vs. `historical_views_past_24h`) through a `StandardScaler` wrapper to enforce uniform value influence during weight assignments.

### 2. Advanced Feature Engineering (Scarcity Acceleration)
- **The Optimization Pitfall:** Initial tracking validation exposed a critical model bias: the regression line suffered a 75% structural reliance on static competitor price matching, rendering the model blind during sudden market stock depletion events.
- **The Solution:** Engineered a **Derived Ratios Feature** tracking custom velocity: `inventory_to_demand_ratio`. By mathematically presenting remaining inventory volume relative to historical item impressions, the algorithm learned to safely scale asset valuation margins autonomously when local scarcity criteria are triggered.

### 3. Production Gateway Unit-Economics Guardrails
- **Risk Mitigation Layer:** Embedded a post-prediction deterministic filter gate within the real-time runtime endpoint payload: `final_price = max(predicted_price, cost_price * minimum_margin)`. 
- **Impact:** Guarantees that even if competitive conditions trigger a downward pricing spiral, corporate cash flow is programmatically insulated against listing products below their structural manufacturing floor.

## Core Performance Metrics Tracked
- **RMSE (Root Mean Squared Error):** Tracks the average absolute currency divergence ($ Delta USD) per catalog prediction against market-clearing thresholds.
- **R-Squared ($R^2$):** Quantifies the specific percentage of operational pricing variance successfully explained by engineered platform data signals.
