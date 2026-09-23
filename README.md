# E-Commerce Sales & Profitability Analysis

Tools: Excel, Pivot Tables, Dashboard

## What this is

I used the Superstore Sales dataset (from Kaggle) to practice Excel and pivot tables, and to look at a question I thought was interesting: some products sell a lot but still lose money because of how much they get discounted. I wanted to actually check that with numbers instead of just assuming it.

## About the data

- 9,994 order records
- Columns include Sales, Profit, Discount, Category, Sub-Category, Region, etc.

## What I did

- Made a `Discount Group` column (0%, 0-10%, 10-20%, 20%+) using nested IF
- Built pivot tables for profit by category/sub-category, by discount group, by region and by month
- Added slicers so you can filter by category, region, year
- Conditional formatting to highlight the loss-making rows
- Put it all together in one dashboard

### A mistake I made

My first version of the "profit margin by discount group" pivot used `Average of Profit Margin` (I had a `Profit Margin` column per row, and just averaged it). That gave me a margin of **-78.5%** for the 20%+ discount group, which seemed way too extreme.

Turns out that's wrong. Averaging a per-row ratio isn't the same as the real margin for the group, a few orders with tiny Sales but a big negative ratio were dragging the average way down, even though they don't matter much in dollar terms. The correct way is `Sum of Profit / Sum of Sales` for the whole group (I did this with a Pivot Table calculated field instead).

With that fix, the real number for 20%+ discount is **-37.3%**, not -78.5%. Direction of the finding didn't change (20%+ discount is still unprofitable), just the size of it.

## What I found

### Sub-categories losing the most money

| Sub-Category | Total Profit |
|---|---:|
| Tables | -$17,726 |
| Bookcases | -$3,473 |
| Supplies | -$1,189 |

### Margin by discount level

| Discount Level | Orders | Aggregate Margin |
|---|---:|---:|
| 0% | 4,798 | +29.5% |
| 0-10% | 94 | +16.6% |
| 10-20% | 3,709 | +11.6% |
| 20%+ | 1,393 | **-37.3%** |

### Breaking it down by category

I split the same margin calculation by category:

| Category | 0% | 0-10% | 10-20% | 20%+ |
|---|---:|---:|---:|---:|
| Furniture | +22.7% | +15.2% | +3.1% | -27.9% |
| Office Supplies | +29.5% | +25.1% | +16.3% | **-119.3%** |
| Technology | +34.0% | +24.4% | +14.6% | -26.4% |

And I also looked at how often each category actually gets discounted that heavily (% of that category's own orders):

| Category | 0% | 0-10% | 10-20% | 20%+ |
|---|---:|---:|---:|---:|
| Furniture | 39.4% | 3.6% | 31.5% | **25.6%** |
| Office Supplies | 51.9% | 0.3% | 36.5% | 11.3% |
| Technology | 45.1% | 0.1% | 45.5% | 9.3% |

If you only looked at the second table, you'd think Furniture is the bigger discounting problem because it gets 20%+ discounts more often. But the first table shows that when Office Supplies does get a 20%+ discount, its margin is much worse (-119.3% vs. -27.9% for Furniture). Neither table tells the full story on its own, so I looked at both.

**One thing I want to flag about this comparison though:** I also looked more closely at the 20%+ discount group because the category comparison did not seem straightforward. The problem is that the 20%+ group contains very different discount levels across categories.

For Furniture, the orders in this group are mostly between 30% and 70% off, with an average discount of 42.5%. For Office Supplies, the orders in this group are either 70% or 80% off, with an average discount of 74.4%. So when Office Supplies shows a much lower profit margin than Furniture in the 20%+ group, the difference may be partly because Office Supplies has much deeper discounts.

Because of this, I would not use this result alone to say that Office Supplies is more sensitive to discounting than Furniture. The category and the actual discount level are mixed together in this comparison.

A better way to compare the categories would be to use smaller discount ranges, for example 20-40%, 40-60% and 60%+. This would make it easier to separate the effect of the discount level from the category itself.

Also worth noting: the 0-10% group only has 94 orders total and within that Office Supplies has just 16 and Technology only 2. Those numbers are small enough that I wouldn't trust them too much.

### Does discounting at least sell more units?

I checked the correlation between `Discount` and `Quantity`: **r ≈ 0.01**, basically nothing. So discounting doesn't seem to be making up for the lost margin by selling more units, at least not in this data.

## Things I'd be careful about

### Other limitations

- The results in this project show associations, not causation. For example, I found that higher discounts are associated with lower profit but I did not control for other factors that could also affect profit, such as cost structure, product mix, seasonality. So I can't say that the discount itself is the only reason profit goes down.

- There are also a few groups with very few orders. In the 0-10% discount group, Office Supplies has only 16 orders and Technology has only 2 orders. These small sample sizes can make the results less stable, so I would not put much weight on those specific numbers.

## If I kept going with this

- Redo the category comparison with finer discount buckets to separate the effect of the category from the effect of discount depth.
- Look into why Tables and Bookcases lose money even before considering discount. It might be a cost/pricing issue, not just a discounting one.

## Conclusion

The main thing this project showed me: averaging per-row profit margins gave a misleading number (-78.5% instead of the real -37.3%), and even after fixing that, a single "20%+" discount bucket can hide real differences between categories. Discounting past 20% is consistently unprofitable in this data, but which category looks worse depends on how closely you look at the numbers behind it.

## Files

```text
├── superstore-sales-analysis.xlsx
│   ├── Superstore sales dataset   (raw data)
│   ├── Pivot                      (sales, profit, margin, and discount analysis)
│   └── Dashboard
