# E-Commerce Sales & Profitability Analysis
Tools: Excel, Pivot Tables

## What's this about

When I first looked at retail data, I assumed the products with the highest sales would also be the most profitable. Turns out that's not always true, some products sell well but still lose money, and the main reason is discounting.

This project uses a Superstore dataset to dig into which product categories are actually profitable, which ones are losing money, and what role discounts play in that.

## Dataset

Superstore Sales Dataset from Kaggle, 9,995 orders from a fictional US-based retailer. Each row is one order line and includes: order date, product category and sub-category, sales amount, quantity, discount applied, profit, customer segment, and region.

## What I did

Step 1: Explored the data structure
Loaded the raw data into Excel, checked data types, looked for any missing values or obvious errors, and got a feel for the range of values (sales, discounts, profit margins).

Step 2: Built Pivot Tables to break down profitability
I created several Pivot Tables to slice the data different ways:
- Profit by Category and Sub-Category to find which products are losing money
- Profit by Discount Group to understand the relationship between discounting and margin
- Sales and Profit by Region to see if performance varies geographically
- Monthly trend to check if there are seasonal patterns

Step 3: Created a Discount Group column
To analyze the discount effect more clearly, I grouped orders into four discount buckets: 0%, 0-10%, 10-20%, and 20%+. This made it easy to compare average profit across discount levels.

Step 4: Built an interactive dashboard
Assembled everything into a single dashboard with slicers for Category, Region, and Year. So anyone can filter the view without touching the raw data.

## What I found

Loss-making sub-categories:

The three sub-categories with negative total profit are:

| Sub-Category | Total Profit |
|-------------|-------------|
| Tables | -$17,726 |
| Bookcases | -$3,473 |
| Supplies | -$1,189 |

Tables stand out, they generate decent sales volume but consistently lose money. When I dug deeper, most of those losses come from orders with high discounts.

The discount problem:

| Discount Level | Avg Profit per Order |
|----------------|---------------------|
| 0% | +$67 |
| 0-10% | +$96 |
| 10-20% | +$25 |
| 20%+ | -$97 |

Once discounts hit 20% or more, orders flip from profitable to loss-making on average. There are 1,393 orders in the 20%+ group, and a large portion of them are in the Furniture category, especially Tables and Bookcases.

The pattern is pretty consistent: the higher the discount, the lower (or more negative) the profit margin. There's no sign that heavy discounting is being offset by higher volume in a meaningful way.

## Takeaway and recommendations

1. Cap discounts at 20% for Furniture items - beyond that threshold, the business is essentially paying customers to take the products.

2. Review the pricing strategy for Tables and Bookcases - these sub-categories lose money even at moderate discounts, which suggests the base price or cost structure may need revisiting, not just the discount policy.

3. Focus promotions on Office Supplies and Technology - these categories maintain healthy margins even at moderate discounts, making them safer candidates for promotional activity.

## Files
- `superstore-sales-analysis.xlsx` - Excel file with Pivot Tables and Dashboard
