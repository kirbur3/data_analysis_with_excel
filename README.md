# data_analysis_with_excel

# Excel Retail Sales Analysis

**Repository Overview**

Self-built Excel dashboard project analyzing retail sales performance (actual vs. target revenue) across 4 regions and 5 categories. Unlike a tutorial-based project, this one was built step by step with each new concept explained before use, but every formula was written, tested, and debugged independently, including real build decisions along the way (e.g., switching from an XLOOKUP-based plan to SUMIFS once the target data turned out to need two-condition matching).

Tools: Excel, SUMIFS, XLOOKUP, EDATE, Data Validation, Text to Columns, Conditional Formatting

Data: Sales Transactions (650 orders: Order ID, Order Date, Region, Category, Sales Rep, Units Sold, Unit Price, Revenue) and Sales Targets (480 rows: monthly revenue targets by Region + Category, Jan 2024–Dec 2025).

---

## Retail Sales Performance Dashboard

Two-sheet analysis layer plus an interactive dashboard, built on top of the raw transactions and targets data.

### Performance Analysis Sheet
- 20 rows (4 regions × 5 categories), each pulling Actual Revenue and Target Revenue via SUMIFS with absolute references into the transactions and targets tables.
- $ Variance (Actual − Target) and % Variance (=IF(Target=0,0,Variance/Target)) columns.
- IF-based Favorable/Unfavorable result column, flagged with two-color conditional formatting (5 Favorable, 15 Unfavorable).
- Totals row summing actual and target revenue across all 20 combinations.

### Dashboard Sheet
- Region and Category selectors built with Data Validation dropdown lists.
- KPI cards (Actual Revenue, Target Revenue, $ Variance, % Variance) driven by SUMIFS referencing the two dropdowns.
- $ Variance by Category clustered column chart, fed by a helper table tied to the Region dropdown.
- Actual vs. Target Revenue Trend line chart across 24 months (Jan 2024–Dec 2025), built from a helper table using EDATE() to generate the month sequence and multi-condition SUMIFS (region, category, and a date range match) to pull monthly actuals and targets.

### Debugging
- Caught and fixed missing absolute references, a conditional formatting rule broken by stray quotation marks, and an Order Date column stored as text rather than a real date (confirmed with ISNUMBER, fixed with Text to Columns) that was causing every date-based SUMIFS to silently return zero.

---

Files: `Excel_Retail_Sales_Analysis_Project.xlsx`
