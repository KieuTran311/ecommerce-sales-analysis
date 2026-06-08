# E-Commerce Sales & Profitability Analysis

Tools: Excel, Pivot Tables, Dashboard

## Project Overview

This project investigates the relationship between discounting and profitability using retail sales data.

## Business Problem

Some products generate strong sales but still lose money because of heavy discounting. This project analyzes sales and profit data to identify products and discount levels that negatively affect profitability.

## Dataset

Superstore Sales dataset from Kaggle.

- 9,995 order records
- Retail sales transactions
- Includes sales, profit, discount, category, sub-category, customer segment, and region

## Technical Approach

### Excel

- Created a Discount Group column using nested IF logic
- Built Pivot Tables for:
  - Profit by Category and Sub-Category
  - Profit by Discount Group
  - Sales and Profit by Region
  - Monthly Trends
- Used Pivot Charts for visualization
- Added slicers for Category, Region, and Year filtering
- Applied conditional formatting to highlight loss-making products
- Built an interactive dashboard for analysis

## Results

### Loss-Making Sub-Categories

| Sub-Category | Total Profit |
|-------------|-------------|
| Tables | -$17,726 |
| Bookcases | -$3,473 |
| Supplies | -$1,189 |

### Profit by Discount Level

| Discount Level | Avg Profit per Order |
|----------------|---------------------|
| 0% | +$67 |
| 0–10% | +$96 |
| 10–20% | +$25 |
| 20%+ | -$97 |

### Key Findings

- Tables generated the largest losses among all sub-categories.
- Orders with discounts above 20% became unprofitable on average.
- Most high-discount transactions were concentrated in the Furniture category.
- Technology and Office Supplies maintained stronger profitability compared to Furniture.

## Recommendations

- Limit Furniture discounts to 20% or lower.
- Focus promotional campaigns on higher-margin categories such as Technology and Office Supplies.
- Review pricing and cost structure for Tables and Bookcases.
- Use the dashboard to monitor discount levels and identify profitability issues early.

## Files

```text
├── superstore-sales-analysis.xlsx
