# Data Dictionary

This document describes the main fields used in the final customer-level dataset created for the Olist Customer Segmentation project.

The processed dataset contains one row for each customer included in the RFM analysis.

## Final Dataset

File: `olist_customer_segmentation_final.csv`

| Column | Description |
|---|---|
| `customer_unique_id` | Unique identifier used to track the same customer across orders |
| `Recency` | Number of days between the customer's latest purchase and the analysis date |
| `Frequency` | Number of delivered orders placed by the customer |
| `Monetary` | Total payment value associated with the customer's delivered orders |
| `R_Score` | Recency score from 1 to 4, where a higher score represents a more recent customer |
| `F_Score` | Frequency score from 1 to 4 based on the customer's number of purchases |
| `M_Score` | Monetary score from 1 to 4 based on customer spending |
| `RFM_Code` | Combined R, F and M scores, such as 413 |
| `Segment` | Customer segment assigned using RFM behavior |
| `Recommended_Action` | Suggested business action for the customer segment |
| `customer_city` | City associated with the customer's latest observed delivered order |
| `customer_state` | Brazilian state associated with the customer's latest observed delivered order |

## RFM Metrics

### Recency

Recency measures how recently a customer purchased.

A lower number of days means the customer purchased more recently.

The analysis date was set to one day after the latest transaction in the cleaned dataset.

### Frequency

Frequency measures how many delivered orders a customer placed.

The dataset contains a large number of one-time buyers, so frequency scoring was adjusted instead of using standard quartiles.

| Frequency | F Score |
|---:|---:|
| 1 order | 1 |
| 2 orders | 2 |
| 3–4 orders | 3 |
| 5+ orders | 4 |

### Monetary

Monetary represents the total payment value associated with a customer's delivered purchases.

Customers were divided into four groups using the monetary distribution of the dataset.

## Customer Segments

| Segment | Description |
|---|---|
| Champions | Recent customers with strong repeat-purchase and spending behavior |
| Loyal Customers | Recent repeat customers with good purchasing behavior |
| Recent Customers | Customers who purchased recently but only once |
| High-Value One-Time | One-time customers with relatively high spending |
| Promising | Fairly recent one-time customers with potential for another purchase |
| Needs Attention | Customers whose only purchase is becoming less recent |
| At Risk | Repeat customers whose latest purchase was a relatively long time ago |
| Inactive | One-time customers who have not purchased for a long period |

## Notes

- Only delivered orders were used for the final RFM analysis.
- Multiple payment records belonging to the same order were aggregated before calculating customer spending.
- One delivered order without payment information was excluded because Monetary could not be calculated reliably.
- Geographic fields represent the latest observed customer location in the available dataset and should not be interpreted as the customer's current location.