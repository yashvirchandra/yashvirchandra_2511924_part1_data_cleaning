# Cleaning Log — Part 1: Business Data Cleaning, Validation & Excel Reporting

## 1. Dataset Overview

The provided retail order dataset was cleaned and validated to create an analysis-ready dataset for business reporting. The raw dataset contained formatting issues, missing values, duplicate records, inconsistent text formats, date issues, and data validation problems.

The original file was preserved as:

`data/raw_orders.xlsx`

The cleaned version was created as:

`data/cleaned_orders.xlsx`

---

## 2. Issues Identified

The following data quality issues were found:

* Inconsistent text formatting in customer and business-related fields.
* Extra spaces and inconsistent capitalization in text columns.
* Missing values in region and ship mode fields.
* Date formatting inconsistencies.
* Shipping records where ship date occurred before order date.
* Duplicate order records.
* Duplicate order IDs requiring review.
* Invalid discount values.
* Sales and profit calculation mismatches.

---

## 3. Cleaning Actions Performed

### Text Cleaning

The following columns were standardized:

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

* Removed extra spaces using TRIM.
* Standardized text capitalization.
* Corrected inconsistent formatting.

---

### Date Cleaning

The following fields were cleaned:

* order_date
* ship_date

Actions performed:

* Converted dates into a consistent date format.
* Identified invalid shipping records.
* Created:

`shipping_delay_days`

which calculates the difference between order date and ship date.

---

## 4. Duplicate Handling

Duplicate analysis performed:

* Exact duplicate rows identified: 20
* Exact duplicate rows removed: 0
* Duplicate order IDs flagged for review: 63 records

Duplicate order IDs were not removed automatically because they required business validation to avoid deleting potentially important records.

---

## 5. Business Rules Applied

### Missing Values

* Missing region values were replaced with "Unknown".
* Missing ship_mode values were replaced with "Unknown".
* Missing discounts were treated as 0 when applicable.

### Discount Validation

* Negative discounts were flagged as invalid.
* Discounts outside the allowed range were flagged.

### Order Status Rules

* Cancelled orders were excluded from completed sales calculations.
* Failed payments were excluded from completed sales calculations.
* Refunded orders were separately identified.

### Shipping Validation

* Ship dates earlier than order dates were marked as invalid shipping records.

---

## 6. Calculated Columns Created

The following columns were added:

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

These columns were created to support analysis and reporting.

---

## 7. Assumptions Made

* Missing discount values were assumed to represent no discount.
* Duplicate order IDs were treated as records requiring review instead of automatic deletion.
* Unknown categories were retained after standardization.

---

## 8. Limitations

* Some duplicate records required manual business confirmation.
* Calculation mismatches were flagged for review.
* Cleaning decisions were based on available dataset information only.

---

## 9. Final Output

The cleaned dataset was prepared for:

* Data quality reporting
* Business analysis
* Pivot reporting
* Decision-making insights
