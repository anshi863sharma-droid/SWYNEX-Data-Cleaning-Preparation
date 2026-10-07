# SWYNEX-Data-Cleaning-Preparation

**Tool used:** Microsoft Excel
**Dataset:** Nike sales data (2,500 rows, 13 columns)

## Files
- `Nike_Sales_cleaned_dataset.xlsx` - cleaned dataset with a summary sheet of the changes

## Issues found and what I did

| Type | Column | Issue | Fix |
|---|---|---|---|
| Inconsistent values | Region | Same city spelled differently (bengaluru, Bangalore, hyderbad, Hyd) | Standardized to Bengaluru and Hyderabad |
| Missing values | Size | 510 blanks | Filled with "Not Specified" |
| Incorrect data types | Size | Letters (M, L, XL) and numbers (6-12) mixed | Converted all to text |
| Invalid values | Discount_Applied | About 180 values above 100% | Removed (left blank), formatted as % |
| Incorrect values | Revenue | 2,334 rows had placeholder 0 | Recalculated as Units_Sold x MRP x (1 - Discount) where all three inputs exist (164 rows); rest left blank |
| Duplicate records | Order_ID | 114 repeated IDs, but the rows are different orders | No rows deleted, no fully identical rows found |

## Left unchanged on purpose
- Blank Units_Sold, MRP, Discount_Applied and Order_Date: not guessed, to avoid creating fake data.
- Units_Sold = -1 (205 rows): treated as returns, so their Revenue is negative.
- Negative Profit: kept, as these can be genuine losses.
