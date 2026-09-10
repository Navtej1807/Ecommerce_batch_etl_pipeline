**# E-Commerce Batch ETL Pipeline

An end-to-end batch ETL pipeline built using **PySpark and Databricks**, following a **Bronze → Silver → Gold** architecture.

The project processes e-commerce data across customers, products, orders, payments, and deliveries, applies data cleaning and quality validation, and produces business-ready analytical datasets.

## Architecture

![ETL Architecture](docs/etl_architecture.png)

## Tech Stack

* **PySpark**
* **Databricks**
* **Delta Lake**
* **SQL**
* **Git & GitHub**
* **Databricks Workflows**

## Pipeline Overview

The pipeline follows a layered architecture:

**Source Tables → Bronze → Silver → Gold**

### Bronze Layer

The Bronze layer ingests the raw source datasets into Delta tables with minimal transformation.

Source tables:

* Customers
* Products
* Orders
* Payments
* Deliveries

### Silver Layer

The Silver layer prepares the data for reliable downstream processing.

Key operations include:

* Data type conversion
* String standardization
* Null handling
* Duplicate removal
* Business-rule validation
* Referential integrity checks
* Data quality validation

Silver outputs:

* `silver_customers`
* `silver_products`
* `silver_orders`
* `silver_payments`
* `silver_deliveries`

Dedicated data-quality tables are also generated for invalid records.

### Gold Layer

The Gold layer contains business-ready datasets for analytics.

Outputs:

* `gold_order_details`
* `gold_customer_summary`
* `gold_product_summary`

These datasets provide order-level, customer-level, and product-level metrics.

## Workflow Orchestration

The pipeline is orchestrated using **Databricks Workflows**.

Execution dependency:

```text
Bronze Transformation
        ↓
Silver Transformation
        ↓
Gold Transformation
```

Each layer runs only after its upstream task completes successfully.

## Repository Structure

```text
Ecommerce_batch_etl_pipeline/
│
├── README.md
├── etl_architecture.png
│    
└── notebooks/
    ├── Bronze_transformation.ipynb
    ├── Silver_transformation.ipynb
    └── Gold_transformation.ipynb
```
******
