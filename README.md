# Amazon Product Sales Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-lightblue) ![Status](https://img.shields.io/badge/Status-Completed-brightgreen) ![Dataset](https://img.shields.io/badge/Dataset-Kaggle-orange)

## Project Overview

End-to-end exploratory data analysis of Amazon product listings to uncover pricing patterns, discount strategies, and customer engagement trends across major product categories. The goal was to identify actionable insights for pricing optimisation and category-level marketing strategy.

---

## Business Question

> **How do discount strategies, pricing, and customer ratings vary across Amazon product categories — and what drives higher customer engagement?**

---

## Dataset

- **Source:** Kaggle — Amazon Products Dataset
- **Size:** 1,465 rows × 16 columns
- **Key Variables:** Product name, category, actual price (₹), discounted price (₹), discount percentage, rating, rating count

---

## Tools & Libraries

| Tool | Purpose |
|------|---------|
| Python | Core programming language |
| Pandas | Data cleaning & manipulation |
| NumPy | Numerical calculations |
| Matplotlib | Data visualisation |
| Seaborn | Statistical charts |

---

## Data Cleaning Steps

- Removed `₹` and `,` characters from price columns; converted to `float`
- Cleaned `discount_percentage` (removed `%`); converted to `int`
- Standardised `rating` column (handled inconsistent formats like `"4.0 out of 5 stars"`); imputed 1 missing value with median (4.1)
- Imputed 2 missing `rating_count` values with median (5,179)
- Extracted `main_category` from nested category strings
- Engineered `discount_amount` column (absolute monetary discount per product)

---

## Key Findings

### 1. Pricing & Discounts
- Discounted prices ranged from **₹39 to ₹77,990**; actual prices up to ₹1,39,900
- Average discount across all products: **47.69%** — indicating discounting is a core sales strategy
- Discount percentages ranged widely from **0% to 94%**, showing significant variation in strategy across products

### 2. Top Product Categories
- **Electronics** dominated with 526 products, highest average actual price (₹10,127) and highest customer engagement (avg 29,998 reviews per product)
- **Computers & Accessories** (453 products) had the highest average discount percentage at **54.02%**
- **Home & Kitchen** (448 products) was the third largest category

### 3. Category-Level Insights
- **OfficeProducts** had the lowest average price (₹397) and lowest average discount (12.35%) — premium positioning with minimal discounting
- **MusicalInstruments** (only 2 products) had a remarkably high average rating count of **44,441** — suggesting viral/niche popularity
- Electronics benefits most from high-value premium positioning due to its price range

### 4. Top Performing Products
- Top 10 products by review count were dominated by **AmazonBasics HDMI cables** and **boAt Bassheads earphones** alongside select Redmi phones
- These products consistently maintained ratings of **4.1–4.4** with review counts exceeding **300,000**

---

## Visualisations

- Histogram: Distribution of discount percentages across all products
- Bar chart: Average actual vs. discounted price by main product category

---

## Insights & Next Steps

- **Discount optimisation:** Correlation analysis between discount level and review volume could identify the optimal discount range that maximises customer engagement without sacrificing margin
- **Category marketing:** Electronics suits premium positioning; Computers & Accessories can leverage high discount messaging
- **Engagement drivers:** Investigate why certain low-category products (e.g. MusicalInstruments) outperform on review counts despite small product numbers

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/karthik-4550/Projects.git

cd Projects

# Install dependencies
pip install pandas numpy matplotlib seaborn

# Open notebook
jupyter notebook Sales_analysis.ipynb
```

---

## About the Author

**Karthik K** — Data Analyst | Chennai, India
[LinkedIn](https://linkedin.com/in/karthik-k-4525k005) | [GitHub](https://github.com/karthik-4550)
