# Customer Order Count – Superstore

**Task 20 – Customer Order Count**
Veda Technology | Data Analytics Track | Level 1, Day 20

## About
I counted how many orders each customer placed in the Sample Superstore dataset (2014-2017) and identified the most frequent buyers. In this dataset every row is an **order line** (one product in an order), so one order can have several rows. To avoid counting duplicate order lines, I counted **distinct Order IDs** per customer, and grouped by **Customer ID**.

## Key numbers
| Measure | Value |
|---------|-------|
| Total customers | 793 |
| Total orders (distinct Order IDs) | 5,009 |
| Total order lines (rows) | 9,994 |
| Average orders per customer | 6.3 |

## Customer order table
The `Customer Orders` tab lists every customer (ID and name) with:
- **Orders** – distinct count of Order ID
- **Order Lines** – number of rows (shown to prove why distinct counting is needed)
- **Total Sales**

It is sorted from the most orders to the fewest.

## Top 10 customers by number of orders
| Rank | Customer ID | Customer Name | Orders | Order Lines | Total Sales |
|------|-------------|---------------|--------|-------------|-------------|
| 1 | EP-13915 | Emily Phan | 17 | 31 | 5,478.1 |
| 2 | ZC-21910 | Zuschuss Carroll | 13 | 31 | 8,025.7 |
| 3 | SH-19975 | Sally Hughsby | 13 | 29 | 3,406.8 |
| 4 | NS-18640 | Noel Staavos | 13 | 26 | 2,964.8 |
| 5 | PG-18820 | Patrick Gardner | 13 | 26 | 3,086.9 |
| 6 | JE-15745 | Joel Eaton | 13 | 23 | 6,760.8 |
| 7 | CK-12205 | Chloris Kastensmidt | 13 | 32 | 3,154.9 |
| 8 | EA-14035 | Erin Ashbrook | 13 | 25 | 2,846.7 |
| 9 | SJ-20125 | Sanjit Jacobs | 12 | 24 | 3,949.7 |
| 10 | RB-19465 | Rick Bensley | 12 | 23 | 4,715.5 |

## Chart
A bar chart of the top 10 customers by number of orders (Top Customers tab).

## Findings
- **Emily Phan is the most frequent buyer** with 17 orders, clearly ahead of everyone else (the next customers have 13).
- **Ties are common.** Seven customers tie with 13 orders (ranks 2 to 8) and two have 12. Order counts are whole numbers, so many customers share the same value. [Edit this line after checking the 11th customer: if it also has 12 orders, there is a tie at the top-10 cutoff.]
- **The most frequent buyer is not the biggest spender.** Zuschuss Carroll placed fewer orders (13) than Emily Phan (17) but spent more (8,025.7 vs 5,478.1), and Joel Eaton also spent more (6,760.8) with 13 orders.
- **Orders are spread across many customers.** The top 10 customers together placed 132 of the 5,009 orders (2.6%), and the average customer placed about 6.3 orders.
- **Counting rows would overstate orders.** For example, Chloris Kastensmidt has 32 order lines but only 13 orders, and the whole dataset has 9,994 rows but only 5,009 orders.

## Equivalent SQL (for reference)
```sql
SELECT customer_id,
       COUNT(DISTINCT order_id) AS orders
FROM sales
GROUP BY customer_id
ORDER BY orders DESC
LIMIT 10;
```

## Files
- `Customer_Order_Count.xlsx` – workbook with the Raw Data, Customer Orders and Top Customers tabs
- `customer_orders_screenshot.png` – screenshot of the Top Customers tab
- `README.md`

## Tools used
Microsoft Excel (PivotTable with Data Model and Distinct Count)

## Author
Rabia
