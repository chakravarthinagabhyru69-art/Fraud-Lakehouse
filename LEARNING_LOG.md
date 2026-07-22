## Day 1 - 2026-07-22
- Lakehouse is combination of two older systems "data lake storage + warehouse" where data lake is cheap storage holding raw files like csv json, huge scale, but messy and unreliable. cheap open storage of a lake, with the reliable tables of a warehouse, in one system.
- i did not run on mac.the code ran on a Databricks serverless compute cluster in the cloud
- there was an error that occured beacuse of atypo by me i put current_data insted of current_date
## Day 1 (night session) - SQL practice
-  GROUP BY:  12 transactions went in, 3 rows came out, one per customer, each with a SUM. So: GROUP BY collapses many rows into one row per distinct value, so aggregate functions like SUM/COUNT can summarize each
- Ran INSERT twice and got 24 rows because: ran insert twice but everything looks normal in the code bout the output changes because of the insert run twice in cloud
- The duplicate james/Kroger row mattered because: there are same identical rows o james which shows his over all spending wrong when we did group by total spend
- ROW_NUMBER with PARTITION BY does: all 12 rows stayed, but each got an rn maria's transactions numbered 1,2,3,4 by amount, james's restarted at 1, aisha's restarted at 1. Then WHERE rn = 1 kept each person's biggest. So: numbers rows within each group (PARTITION BY = the group, ORDER BY = the ranking), keeping all rows instead of collapsing. Remember: rank without collapsing.
- Errors I hit today: missing comma (PARSE_SYNTAX_ERROR), 5 vs 6 columns, misspelled column names (UNRESOLVED_COLUMN)
