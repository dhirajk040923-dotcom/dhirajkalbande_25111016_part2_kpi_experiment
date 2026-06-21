# dhirajkalbande_25111016_part2_kpi_experiment
1. Issues Found
The following data quality issues were identified in the raw dataset:
•	Missing values in one or more fields.
•	Duplicate records and duplicate Order IDs.
•	Invalid discount values (negative values, values greater than 100%, or missing values).
•	Inconsistent date formats.
•	Invalid or missing Order Date and Ship Date values.
•	Ship dates occurring before order dates.
•	Invalid order status values.
•	Sales values not matching expected calculations.
•	Profit values not matching expected calculations.
•	Inconsistent text formatting and spacing in selected fields.
________________________________________
2. Cleaning Actions Performed
The following cleaning actions were performed:
Missing Values
•	Missing values were identified and documented.
•	Records containing missing values were flagged for review.
Duplicate Records
•	Duplicate records were detected using Order ID and full-row comparisons.
•	Duplicate entries were flagged as potential data quality issues.
Discount Validation
•	Discount values were validated.
•	Invalid discount values were flagged.
•	A cleaned discount field was created for analysis purposes.
Date Standardization
•	Order Date and Ship Date fields were converted into a consistent date format.
•	Invalid date entries were identified and flagged.
•	Shipping delay was calculated using valid dates.
Order Status Validation
•	Order status values were reviewed against accepted business values.
•	Invalid statuses were flagged.
Sales and Profit Validation
•	Expected sales values were recalculated using:
Sales = Quantity × Unit Price × (1 − Discount)
•	Expected profit values were recalculated using:
Profit = Sales − Cost
•	Mismatches between reported and calculated values were identified and flagged.
Derived Fields Created
The following analytical fields were created:
•	cleaned_discount
•	Calculated sales
•	calculate Profit
•	Profit margin
•	shipping_delay_days
•	Order month
•	Order Year
•	data_quality_flag
________________________________________
3. Business Rules Applied
The following business rules were used during cleaning:
Discount Rules
•	Discount must be between 0 and 1 (0%–100%).
•	Any value outside this range is considered invalid.
Date Rules
•	Order Date must exist and be a valid date.
•	Ship Date must exist and be a valid date.
•	Ship Date cannot occur before Order Date.
Sales Rules
•	Sales should equal:
Quantity × Unit Price × (1 − Discount)
Profit Rules
•	Profit should equal:
Sales − Cost
Order Status Rules
Accepted statuses include:
•	Completed
•	Pending
•	Cancelled
•	Returned
•	Refunded
•	Failed
Any other value is treated as invalid.
________________________________________
4. Assumptions Made
The following assumptions were made during cleaning:
•	Discount values are stored as decimal percentages.
o	Example: 0.20 = 20%
•	Sales and profit differences may be caused by rounding.
•	Date values that could not be converted into valid dates were treated as invalid.
•	Records with data quality issues were retained whenever possible and flagged instead of deleted.
•	Existing business data was preserved unless clearly invalid.
________________________________________
5. Records Removed
•	No records were permanently removed from the cleaned dataset.
•	Data quality issues were tracked using flags to preserve auditability.
________________________________________
6. Records Flagged
Records were assigned data quality flags based on identified issues.
Flag Categories
CLEAN
Records with no detected issues.
WARNING
Records containing minor issues requiring review.
Examples:
•	Missing values
•	Duplicate records
•	Minor calculation discrepancies
INVALID
Records containing critical data quality issues.
Examples:
•	Invalid dates
•	Invalid discounts
•	Invalid order status values
•	Significant sales or profit calculation mismatches
________________________________________
7. Limitations of the Cleaning Process
The following limitations should be noted:
•	Business rules were inferred from available data and assignment requirements.
•	Some calculation mismatches may be caused by external business logic not available in the dataset.
•	Invalid dates could not always be corrected automatically.
•	Duplicate detection was based on available fields and may not capture all business-level duplicates.
•	Customer, product, and payment information were not validated against external master data sources.
•	Data quality flags identify potential issues but do not guarantee that all errors have been detected.

