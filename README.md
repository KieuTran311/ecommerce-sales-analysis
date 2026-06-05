# E-Commerce Sales & Profitability Analysis
Tools: Excel, Pivot Tables, Dashboard

## The Business Problem

Growing revenue and growing profit are not the same thing. A business can run promotions, move more units, and still end up less profitable than before if the discount strategy is wrong.

This project investigates exactly that: "_A retailer is offering discounts across product categories, but are those discounts actually helping the bottom line, or quietly destroying it?_" The goal is to identify which products are losing money, understand why and give the business a clearer picture of where to focus and where to stop spending.

## Dataset

Superstore Sales Dataset from Kaggle, 9,995 orders from a fictional US-based retailer. Each row is one order line and includes: order date, product category and sub-category, sales amount, quantity, discount applied, profit, customer segment, and region.

## What I Did

**Step 1: Explored the data structure**

Loaded the raw data into Excel, checked data types, reviewed the range of values across sales, discounts, and profit to understand the shape of the data before any analysis.

**Step 2: Built Pivot Tables to break down profitability**

Created several Pivot Tables to slice the data different ways:
- Profit by Category and Sub-Category: to find which products are losing money
- Profit by Discount Group: to understand the relationship between discounting and margin
- Sales and Profit by Region: to check if performance varies geographically
- Monthly trend: to identify seasonal patterns

**Step 3: Created a Discount Group column**

Grouped orders into four discount buckets: 0%, 0-10%, 10-20%, and 20%+. This made it easier to compare average profit across discount levels without eyeballing individual rows.

**Step 4: Built an interactive dashboard**

Assembled everything into a single Excel dashboard with slicers for Category, Region, Year, so anyone can filter the view without touching the raw data.

## What I Found

**Loss-making sub-categories:**

| Sub-Category | Total Profit |
|-------------|-------------|
| Tables | -$17,726 |
| Bookcases | -$3,473 |
| Supplies | -$1,189 |

Tables stand out the most. They generate decent sales volume but consistently lose money. When I dug deeper, the losses are concentrated in orders with high discounts, not a pricing problem across the board but a discount discipline problem.

**The discount problem:**

| Discount Level | Avg Profit per Order |
|----------------|---------------------|
| 0% | +$67 |
| 0–10% | +$96 |
| 10–20% | +$25 |
| 20%+ | -$97 |

Once discounts hit 20% or more, orders flip from profitable to loss-making on average. There are 1,393 orders in the 20%+ group - a significant portion of total transactions and most of them are in the Furniture category.

The pattern is consistent: the higher the discount, the lower the margin. There's no evidence that heavy discounting is being offset by meaningfully higher volume.

**Where the money actually comes from:**

Not all categories behave the same way. Technology and Office Supplies maintain healthy margins even at moderate discounts. Furniture - particularly Tables and Bookcases is where the discount strategy breaks down.

## What the Business Should Do Differently

**_1. Cap discounts at 20% for Furniture_**:

Beyond 20%, orders in this category average a loss of $97 each. A hard cap would immediately stop the bleed. This doesn't mean stopping promotions entirely it means setting a floor below which discounts don't go.

**_2. Shift promotional focus to high-margin categories_**

Technology and Office Supplies can handle moderate discounts without destroying margin. If the goal is to run a promotion and drive volume, these are the safer categories to discount not Furniture.

_For example:_ A 10% discount on a Technology product that holds a healthy margin is a much better use of promotional budget than a 25% discount on a Table that results in a net loss.

**_3. Review Tables and Bookcases pricing or cost structure_**

These sub-categories lose money even before heavy discounting kicks in. That suggests either the base price is too low relative to cost, or the cost of goods needs to be renegotiated.

**_4. Use the dashboard to monitor discount compliance_**

The Excel dashboard can be used by the sales or category team to track discount levels by sub-category in real time. If a region or category consistently exceeds the 20% threshold, it becomes visible and actionable rather than buried in raw transaction data.

## Files
```
├── superstore-sales-analysis.xlsx    # Excel file with Pivot Tables and Dashboard
```
