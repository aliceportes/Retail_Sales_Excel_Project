# Retail Sales Dashboard (Excel Project)

---

## Overview
This Excel project showcases a complete data analysis workflow using the "Retail Store Sales (Dirty for Data Cleaning)" dataset from Kaggle. It includes data cleaning, pivot tables, and a fully interactive dashboard built with slicers, KPI cards, and multiple chart types.

---

## Dataset

- **Source**: [Retail Store Sales – Dirty for Data Cleaning (Kaggle)](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning/data)
- **Note**: Data from 2025 was excluded from the analysis, as it only contained records for January. Including it would distort yearly and monthly trends and lead to misleading insights.

---

## Data Cleaning Steps

Performed entirely in Excel, the data cleaning process included:

- **Duplicate Check**: No duplicates found.
- **Column Type Formatting**:
  - Converted `Transaction ID`, `Customer ID`, `Category`, `Item`, `Payment Method`, and `Location` to **Text**
  - Converted `Price Per Unit` and `Total Spent` to **Currency**
  - Converted `Quantity` to **Number**
- **Alignment Check**: Left-aligned text and right-aligned numeric columns for consistency.
- **Trimmed Extra Spaces**: Used `=LEN(cell)<>LEN(TRIM(cell))` on `Category`, `Item`, `Payment Method`, and `Location`.
- **Missing Value Handling**:
  - `Discount Applied`: Replaced missing values with `"Unknown"`, and standardized existing values by converting `TRUE`/`FALSE` to `"Yes"`/`"No"`.
  - `Item`: Sorted by `Category` and `Price Per Unit`, then used **forward fill** (`=↑` + Ctrl+Enter) to fill missing items logically.
  - `Price Per Unit`: Filled missing values using:  
    `=IF(ISBLANK([@[Price Per Unit]]), [@[Total Spent]] / [@Quantity], [@[Price Per Unit]])`
  - `Quantity`: Could not calculate due to missing `Total Spent`, so filled with **average quantity per Category** using:  
    `=IF(ISBLANK([@[Quantity]]), ROUND(AVERAGEIFS([Quantity], [Category], [@[Category]]), 0), [@[Quantity]])`
  - `Total Spent`: Once `Quantity` and `Price Per Unit` were available, used:  
    `=IF(ISBLANK([@[Total Spent]]), [@[Price Per Unit]] * [@[Quantity]], [@[Total Spent]])`
- **Final Touch**: Sorted the final cleaned table by:
  - `Category` (A → Z)
  - `Item` (A → Z)
  - `Transaction Date` (Newest → Oldest)

---

## Pivot Tables Created

- **Sales by Year**
- **Sales by Month**
- **Sales by Category**
- **Top 10 Products by Quantity Sold**
- **Preferred Payment Method**

---

## Dashboard Overview

A clean and visually consistent dashboard was built using:
- **Theme**: Light blue background with orange and green accents
- **Design Elements**:
  - Theme icon and title with rounded border
  - KPI Cards:
    - Total Sales Revenue
    - Total Transactions
    - Distinct Products Sold
  - Charts:
    - Sales by Year (**Line Chart**)
    - Sales by Month (**Line Chart**)
    - Sales by Category (**Clustered Bar Chart**)
    - Top 10 Products by Quantity Sold (**Stacked Column Chart**)
    - Preferred Payment Method (**Pie Chart**)
  - Slicers:
    - `Location`
    - `Discount Applied`

---

## Tools & Techniques Used

- Microsoft Excel (data cleaning, pivot tables, dashboard design)
- Slicers, formulas, custom number formatting
- Shape styling (rounded cards, icons, colors)
- Conditional logic for missing data
- Clean UX design for interactive dashboards

---

## Key Insights

- **Consistent Year-over-Year Growth**  
  Total sales have remained consistent over the past three years, with a noticeable increase of approximately **7.6% from 2023 to 2024**. This upward trend indicates steady business growth and a promising outlook.

- **Peak Sales in January and December**  
  **January and December** consistently recorded the highest monthly sales, likely due to seasonal spikes, holiday demand, or promotional periods.

- **Top Revenue-Generating Categories: Butchers and Electric Household Essentials**  
  These two product categories generated the **highest total revenue**, reflecting strong customer preference and high purchase frequency in essential goods.

---

## Conclusion

This project demonstrated the full Excel analytics workflow, from cleaning messy data to building an interactive dashboard. By transforming a disorganized dataset into meaningful insights, I strengthened my ability to identify and handle real-world data quality issues and design clean, user-friendly dashboards for business reporting.

If you have any feedback or suggestions, feel free to connect. I'm always looking to improve and learn from every project.

Thank you!


