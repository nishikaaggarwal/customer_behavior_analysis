# Customer Shopping Behavior Analysis

End-to-end **Business Analyst** portfolio project: cleaning and transforming raw retail transaction data in Python, running structured business analysis in SQL, and visualizing insights in an interactive Power BI dashboard.

## 📌 Problem Statement

A leading retail company wants to better understand its customers' shopping behavior in order to improve sales, customer satisfaction, and long-term loyalty. Management has noticed shifts in purchasing patterns across demographics, product categories, and sales channels, and wants to know which factors — discounts, reviews, seasons, or payment preferences — drive consumer decisions and repeat purchases.

**Business question:** How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?

## 🗂️ Dataset

- **Source:** Kaggle
- **Records:** 3,900 customer transactions
- **Columns:** 18 — customer demographics, purchase details, and shopping behavior
- **Key fields:** Age, Gender, Location, Subscription Status, Item Purchased, Category, Purchase Amount, Season, Size, Color, Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type
- **Data quality issue:** 37 missing values in `Review Rating`

## 🛠️ Tools & Tech Stack

| Stage | Tool(s) |
|---|---|
| Data preparation & modeling | Python (pandas, Jupyter Notebook) |
| Structured business analysis | SQL (PostgreSQL) |
| Visualization & dashboard | Power BI |
| Reporting & presentation | Excel, PowerPoint |

## 🧹 Data Preparation (Python)

- Loaded and explored the dataset with `df.info()` and `df.describe(include='all')`
- Checked for nulls (`df.isnull().sum()`) — found 37 missing `Review Rating` values
- **Imputed missing ratings using the median rating within each product category** (rather than a blanket column mean), so clothing items were filled from clothing medians, not footwear
- Standardized all column names to `snake_case`
- Engineered new features: `age_group` (binned from Age) and `purchase_frequency_days` (mapped from text values like "Weekly", "Fortnightly", "Quarterly" to numeric day counts)
- Found `discount_applied` and `promo_code_used` were identical across all rows — dropped the redundant `promo_code_used` column and mapped `discount_applied` to a binary numeric flag
- Connected the Jupyter notebook to PostgreSQL and loaded the cleaned DataFrame for SQL analysis

## 🧮 SQL Analysis — Business Questions Answered

1. Revenue by Gender
2. High-spending customers who still used discounts
3. Top 5 products by average review rating
4. Standard vs. Express shipping — average purchase amount comparison
5. Subscribers vs. non-subscribers — average spend and total revenue
6. Top 5 most discount-dependent products
7. Customer segmentation — New / Returning / Loyal
8. Top 3 products per category
9. Repeat buyers (>5 purchases) vs. subscription status
10. Revenue by age group

## 📊 Power BI Dashboard

An interactive dashboard with filters for Subscription Status, Gender, Category, and Shipping Type, showing:
- **3.9K** customers
- **$59.76** average purchase amount
- **3.75** average review rating
- Revenue and sales breakdowns by category and age group
- Subscription status split (27% subscribed / 73% not)

*(See `/dashboard` folder for the `.pbix` file and dashboard screenshot.)*

## 💡 Key Business Recommendations

- **Boost subscriptions** — only 27% of customers are subscribed despite comparable average spend to non-subscribers
- **Build loyalty programs** — reward repeat buyers to move them from Returning into the Loyal segment
- **Review discount policy** — products like Hat, Sneakers, and Coat have ~50% of purchases discounted; balance sales lift against margin
- **Highlight top-rated and best-selling products** in campaigns (Gloves, Sandals, Boots / Blouse, Pants, Jacket, Jewelry)
- **Target marketing by segment** — focus on Male customers, Express-shipping users, and the Young Adult age group, which drive the highest spend

## 📁 Repository Structure

```
├── data/
│   └── customer_shopping_behavior.csv
├── notebooks/
│   └── data_cleaning_and_prep.ipynb
├── sql/
│   └── business_analysis_queries.sql
├── dashboard/
│   ├── customer_behavior_dashboard.pbix
│   └── dashboard_screenshot.png
├── report/
│   └── Customer_Shopping_Behavior_Analysis_Report.docx
└── README.md
```

## 👤 Author

**Nishika** — Business Analyst | Data Analytics Enthusiast
