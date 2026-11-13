# E-commerce Delivery & Logistics Performance Analysis

![Python](https://img.shields.io/badge/Python-3.9%2B-blue) ![Pandas](https://img.shields.io/badge/Pandas-data%20analysis-150458) ![Power BI](https://img.shields.io/badge/Power%20BI-dashboard-F2C811) ![Status](https://img.shields.io/badge/status-in%20progress-orange)

Data analytics project for **Qveto Technologies** (Intern Project 1). It measures delivery reliability for an online retailer, finds where delays cluster, and links delivery performance to customer ratings.

## Table of Contents
1. [Business Problem](#business-problem)
2. [Dataset](#dataset)
3. [Methodology](#methodology)
4. [KPI Definitions](#kpi-definitions)
5. [Key Findings](#key-findings)
6. [Recommendations](#recommendations)
7. [Repository Structure](#repository-structure)
8. [How to Run](#how-to-run)
9. [Limitations](#limitations)
10. [Author](#author)

## Business Problem
Late deliveries and cancellations reduce customer satisfaction and trust. This project answers four questions:
- How reliable is delivery overall (on-time rate, delivery time, cancellations)?
- Where do delays concentrate (region, product category, weekday, month)?
- Are delays caused mainly by slow dispatch or slow shipping?
- How do late deliveries relate to customer ratings?

## Dataset
**Brazilian E-Commerce Public Dataset by Olist** (Kaggle), about 99,000 orders from Sept 2016 to Oct 2018.

Tables used: orders, customers, order reviews, order items, products, sellers, product category translation.
Raw files are not stored in this repository. Download them from Kaggle by searching for the dataset name above.

## Methodology
1. **Data audit:** checked missing values, duplicate IDs, impossible timestamps and extreme durations. Unusual records were flagged, not deleted.
2. **KPI engineering:** defined each KPI with a documented denominator.
3. **Segment analysis:** compared performance by destination state, seller state, product category, weekday and month.
4. **Delay diagnosis:** split delivery time into processing time (purchase to carrier) and transit time (carrier to customer).
5. **Customer experience:** compared review scores of late and on-time orders.
6. **Dashboard:** Power BI dashboard built on the final analytical dataset.

## KPI Definitions
| KPI | Definition | Denominator |
|---|---|---|
| On-time rate | Delivered on or before the estimated date | 96,470 delivered orders with a valid delivery date |
| Cancellation rate | Canceled orders / all placed orders | 99,441 orders |
| Delivery duration | Delivery date minus purchase date (days) | 96,470 delivered orders |
| Delay | Delivery date minus estimated date, late orders only | Late delivered orders |
| Processing time | Carrier handover minus purchase date (days) | Delivered orders without timestamp errors |
| Rating comparison | Review score, late vs on-time orders | Delivered orders with a review |

## Key Findings
| Measure | Result |
|---|---|
| On-time rate | 91.89% |
| Cancellation rate | 0.63% |
| Average delivery time | 12.09 days (median 10) |
| Average delay of late orders | 9.55 days |
| Same-state vs cross-state delivery | 7.48 vs 14.68 days |
| Transit time, on-time vs late orders | 7.89 vs 25.68 days |
| Average review, on-time vs late orders | 4.29 vs 2.57 |
| Low reviews (1-2 stars), on-time vs late orders | 9.2% vs 52.9% |

- **Region matters most.** The Northeast has the weakest on-time rates: AL 76.1%, MA 80.3%, PI 84.0%, CE 84.7%, BA 86.0%.
- **Rio de Janeiro is the largest problem by volume:** 12,350 orders, 86.5% on time, about 1,660 late orders.
- **Late deliveries are concentrated:** SP and RJ account for about 52% of late orders.
- **Shipping, not dispatch, drives delay:** transit explains about 86% of the extra time on late orders.
- **Cross-state orders** take about twice as long and make up roughly 73% of late deliveries.
- **Peak months were weak:** on-time rate fell to 85.7% in Nov 2017 and 78.6% in Mar 2018.
- **Weekday has only a small effect** (90.9% to 92.5%).
- **Late orders are linked to low ratings.** All findings are associations, not proven causes.

## Recommendations
1. Review shipping performance to RJ and the Northeast states, starting with RJ.
2. Set estimated delivery dates by destination state so promises match reality.
3. Test fulfilment closer to slow regions to reduce cross-state shipping.
4. Plan carrier capacity before peak months and alert when monthly on-time rate drops below 90%.
5. Set a seller dispatch target of about 3 days.
6. Review shipping arrangements for bulky goods such as office furniture.

## Repository Structure
```
ecommerce-delivery-analysis/
├── notebooks/
│   ├── 01_data_audit.ipynb
│   ├── 02_kpis_and_segments.ipynb
│   └── 03_findings.ipynb
├── docs/
│   └── data_dictionary_and_cleaning_log.md
├── .gitignore
└── README.md
```

## How to Run
1. Download the Olist dataset from Kaggle.
2. Open Google Colab and upload the CSV files.
3. Open and run the notebooks in order: 01, 02, 03 (Runtime, then Run all).

Libraries used: pandas, numpy.

## Limitations
- The dataset has **no carrier field**, so carrier comparison is not possible. Customer state and seller state are used as the regional dimension.
- Distance was not measured directly. Seller and customer state are only a proxy.
- Estimated delivery dates are generous, so on-time rate alone can hide slow delivery. Average delivery days are reported as well.
- Findings are associations, not proven causes.
- Sept to Dec 2016 has very few orders, so trend analysis covers Jan 2017 to Aug 2018.
- Each order uses the category and seller of its first item.

## Author
**Shalini Singh**, Data Analytics Intern, Qveto Technologies
GitHub: [shalini2004singh](https://github.com/shalini2004singh)
