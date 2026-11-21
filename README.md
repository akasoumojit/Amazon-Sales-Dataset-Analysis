# Amazon Sales Exploratory Data Analysis

## Problem Statement
An e-commerce business wants to know what really drives revenue and where it leaks. Using 100,000 synthetic Amazon orders (2020–2024, 20 columns) we ran a structured EDA — data understanding, univariate, bivariate, multivariate and temporal analysis, plus hypothesis testing — and converted the findings into business recommendations.

**Approach:** data quality checks → feature engineering (gross/net value, discount amount, shipping ratio, time features) → visual exploration → statistical tests (Spearman, Kruskal-Wallis, Chi-square, Mann-Whitney) → recommendations.

## Summary of Findings
- **Clean but synthetic data:** no missing values/duplicates; `TotalAmount` reconciles exactly with `Quantity × UnitPrice × (1−Discount) + Tax + Shipping`. Geography and product–category labels are inconsistent (synthetic).
- **Order value:** median ≈ 714, mean ≈ 918 (skew 0.95); top 10% of orders contribute ~27% of revenue.
- **Discounts do not lift volume:** correlation with quantity ≈ 0 (p = 0.63); ~3 units per order at every discount level, while average order value falls ~26% from 0% to 30% discount. 40% of orders are full price.
- **Fulfilment leakage:** 74.6% Delivered; 3% Cancelled, 3% Returned (~6.1% of revenue, ≈5.6M); 19% still Shipped/Pending.
- **Shipping** is flat/random (0–15) and uncorrelated with order size (r = 0.04), so small orders carry a much higher shipping burden.
- **Concentration:** US = 70% of orders, India 15%.
- **Flat business:** yearly revenue 18.2–18.5M (2024 −2% vs 2020); no seasonal or promotional spikes after normalising for month length; no weekday effect.
- **Category, brand, payment method, country and seller differences are small (~2–3%) and statistically insignificant**; seller cancellation spread is consistent with chance.

## Key Recommendations
1. Reduce blanket discounts (especially ≥20%); A/B test targeted promotions.
2. Fix fulfilment: audit Pending/Shipped backlog, reduce cancellations/returns.
3. Introduce free-shipping thresholds / tiered shipping.
4. Raise AOV through bundles and cross-sell rather than discounting.
5. Plan seasonal campaigns to break the revenue plateau; diversify beyond the US.
6. Collect margin, cost, rating and return-reason data to enable deeper analysis.

## Repository Contents
| File | Description |
|---|---|
| `Amazon Sales Dataset Analysis (1).ipynb` | Full executed analysis notebook |
| `Amazon.csv` | Original dataset |
| `presentation` | Summary deck (add `.pptx` / `.pdf`) |
| `README.md` | This file |

## How to Run
```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter notebook Amazon_EDA.ipynb
```
