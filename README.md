# sql-exploratory-data-analysis-project

# Sales Analytics Data Model (Dimensional Modeling Project)

This project builds a clean, analysis-ready dimensional model for a retail sales environment.  
Using customer, product, and sales datasets, the project produces a structured **star schema** suitable for BI dashboards, reporting, and downstream analytics.

---

## 📌 Project Overview

The goal of this project is to design and prepare a high-quality analytics dataset using principles commonly used in business intelligence and data warehousing:

- Dimensional modeling (fact and dimension tables)
- Data cleaning & standardization
- Joining datasets into a unified schema
- Enabling sales performance insights (customer behavior, product trends, revenue patterns)

This dataset can be used as the foundation for Power BI dashboards, SQL analysis, or machine learning experiments.

---

## 🧱 Data Model (Star Schema)

**Fact Table**
- `fact_sales`  
  Contains transactional-level sales information such as order dates, quantities, prices, and revenue.

**Dimension Tables**
- `dim_products`  
  Contains product attributes including category, subcategory, product line, and cost.

- `dim_customers`  
  Contains customer demographics such as name, location, gender, marital status, and birthdate.

```mermaid
erDiagram
    FACT_SALES {
        int order_number
        int product_key
        int customer_key
        date order_date
        date shipping_date
        date due_date
        float sales_amount
        int quantity
        float price
    }

    DIM_PRODUCTS {
        int product_key
        int product_id
        string product_number
        string product_name
        string category
        string subcategory
        string product_line
        float cost
        date start_date
    }

    DIM_CUSTOMERS {
        int customer_key
        int customer_id
        string customer_number
        string first_name
        string last_name
        string country
        string marital_status
        string gender
        date birthdate
        date create_date
    }

    FACT_SALES }o--|| DIM_PRODUCTS : "product_key"
    FACT_SALES }o--|| DIM_CUSTOMERS : "customer_key"
