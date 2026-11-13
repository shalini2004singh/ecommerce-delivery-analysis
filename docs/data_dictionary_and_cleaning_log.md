# Data Dictionary and Cleaning Log

**Project:** E-commerce Delivery & Logistics Performance Analysis
**Organisation:** Qveto Technologies, Data Analytics Internship (Project 1)
**Dataset:** Brazilian E-Commerce Public Dataset by Olist (Kaggle)
**Author:** Shalini Singh

## Contents
1. [Source Tables](#1-source-tables)
2. [Field Dictionary](#2-field-dictionary)
3. [Derived Fields](#3-derived-fields)
4. [Data Quality Audit](#4-data-quality-audit)
5. [Cleaning Rules](#5-cleaning-rules)
6. [Assumptions and Known Limitations](#6-assumptions-and-known-limitations)
7. [Validation](#7-validation)

## 1. Source Tables
| Table | Purpose in this project |
|---|---|
| olist_orders_dataset | Order status and all delivery timestamps (99,441 orders) |
| olist_customers_dataset | Destination state of each order |
| olist_order_reviews_dataset | Customer review scores |
| olist_order_items_dataset | Link between orders, products and sellers |
| olist_products_dataset | Product category |
| olist_sellers_dataset | Seller state |
| product_category_name_translation | English category names |

Raw files are stored unchanged and are not committed to this repository.

## 2. Field Dictionary

### 2.1 Orders
| Field | Type | Description |
|---|---|---|
| order_id | string | Unique order identifier. No duplicates found. |
| customer_id | string | Links to the customers table. |
| order_status | string | delivered, shipped, canceled, unavailable, invoiced, processing, created or approved. |
| order_purchase_timestamp | datetime | When the order was placed. |
| order_approved_at | datetime | When payment was approved. |
| order_delivered_carrier_date | datetime | When the order was handed to the carrier. |
| order_delivered_customer_date | datetime | When the customer received the order. |
| order_estimated_delivery_date | datetime | Delivery date promised to the customer. |

### 2.2 Other tables
| Field | Table | Type | Description |
|---|---|---|---|
| customer_state | customers | string | Destination state, used as the region. |
| review_score | reviews | integer | Customer rating from 1 to 5. |
| review_creation_date | reviews | datetime | Used to keep the latest review per order. |
| product_id | items, products | string | Product identifier. |
| seller_id | items, sellers | string | Seller identifier. |
|
