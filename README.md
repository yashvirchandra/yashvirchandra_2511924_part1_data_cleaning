# Part 1: Business Data Cleaning, Validation & Excel Reporting

## Problem Summary

This project focuses on cleaning and validating retail order-level sales data for a business analysis purpose.

The raw dataset contained several data quality issues such as inconsistent text formatting, missing values, duplicate records, date inconsistencies, invalid discounts, and sales/profit calculation mismatches.

The objective was to transform the raw data into a clean, validated, and analysis-ready dataset along with Excel reports and pivot summaries.

---

## Dataset Description

The dataset used for this project is:

`raw_orders.xlsx`

The dataset contains retail transaction-level information including:

* Order details
* Customer information
* Product categories
* Sales and profit details
* Shipping information
* Payment and order status

The original dataset was preserved without modification.

The cleaned dataset created after processing is:

`cleaned_orders.xlsx`

---

## Tools Used

Tools used:

* Microsoft Excel
* Excel formulas
* Pivot Tables
* Data validation techniques
* GitHub

Excel features used:

* TRIM
* Text formatting
* Find and Replace
* Conditional logic formulas
* PivotTable analysis

---

# Cleaning Steps Performed

## 1. Text Cleaning

The following fields were cleaned:

* customer_name
* segment
* region
* state
* city
* category
* sub_category
* ship_mode
* payment_status
* order_status

Cleaning actions:

* Removed extra spaces
* Standardized text capitalization
* Cleaned inconsistent text formats

---

## 2. Date Cleaning and Validation

The following columns were validated:

* order_date
* ship_date

Actions performed:

* Converted dates into a consistent date format
* Checked missing and invalid date values
* Identified shipping records where ship date was earlier than order date

Created:

`shipping_delay_days`

to calculate the difference between order date and ship date.

---

## 3. Duplicate Handling

Duplicate checks were performed.

Results:

* Exact duplicate rows found: 20
* Exact duplicate rows removed: 0
* Duplicate order IDs flagged for review

Duplicate order records were flagged instead of being automatically removed to avoid losing potentially important business information.

---

## 4. Calculated Columns Created

The following columns were added:

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

These columns were created for validation and reporting purposes.

---

# Business Rules Applied

The following business rules were implemented:

* Missing region values were replaced with "Unknown".
* Missing ship_mode values were replaced with "Unknown".
* Missing discount values were treated as 0 where applicable.
* Negative discounts were flagged as invalid.
* Discounts outside the allowed range were flagged.
* Cancelled orders were excluded from completed sales analysis.
* Failed payments were excluded from completed sales analysis.
* Refunded orders were separately identified.
* Ship dates earlier than order dates were marked as invalid shipping records.

---

# Summary of Data Quality Issues Found

Major issues identified:

| Issue                    | Result              |
| ------------------------ | ------------------- |
| Missing region values    | Filled with Unknown |
| Missing ship mode values | Filled with Unknown |
| Duplicate rows           | Identified          |
| Duplicate order IDs      | Flagged for review  |
| Invalid discounts        | Flagged             |
| Date issues              | Validated           |
| Calculation mismatches   | Identified          |

The cleaned dataset was prepared for business reporting.

---

# Summary of Final Pivot Reports

The pivot summary workbook contains:

## Sales and Profit Analysis

* Sales and profit by region
* Sales and profit by category and sub-category

## Order Analysis

* Order count by ship mode
* Refunded, cancelled, and failed order summary by region

## Customer Analysis

* Profit margin by customer segment

## Trend Analysis

* Monthly sales trend

These reports help understand revenue performance, profitability, and operational issues.

---

# Key Business Insights

The analysis helps the company identify:

* Which regions contribute the highest sales and profit
* Which categories generate stronger revenue
* Customer segments with better profitability
* Shipping and order issues affecting operations
* Data quality problems requiring attention

---

# Assumptions and Limitations

## Assumptions

* Missing discount values were considered as no discount when other sales details were valid.
* Duplicate order IDs were treated as records requiring review.
* Unknown values were retained after cleaning.

## Limitations

* Some flagged records require manual business verification.
* The analysis is limited to the provided dataset only.
* Automated cleaning rules may require additional review for complex cases.

---

# Screenshots Included

The repository contains screenshots showing:

* Raw dataset preview
  `raw_data_preview.png`

* Cleaned dataset with calculated columns
  `cleaned_data_preview.png`

* Pivot summary report 1
  `pivot_summary_1.png`

* Pivot summary report 2
  `pivot_summary_2.png`

---
