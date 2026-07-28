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
## Day 2 — SQL Joins

**JOIN vs LEFT JOIN**
- Plain JOIN: Plain JOIN keeps only customers that have atleast one matching transection match so since devon has no matching  transections it consider his account as dormant (which rows survive? what happens to devon?)
- LEFT JOIN: where as in LEFT JOIN it keeps all the rows from left table (customers), even the one with no matches transections (which rows survive? why does devon stay?)
- One line: matched vs unmatched means...

**NULL as a fraud signal**
- After a LEFT JOIN, a null merchant means the merchant with no matching row on the transection side example devon in our project
- In banking that = a dormant account, which matters because it is the account that was opened and never used so that being said in banking if an account opened not used it goes under dormant and is consider as primary target for account takeover fraud.

**The typo lesson (missing "s")**
- customer vs customers — why did SQL NOT throw an error? SQL won't throw error  the if there is a similar table  and the typo it will consider other table coz rather thank this since this table is also existed it wont show error simply it will consider other table 
- What I'll do differently: the way i do is test the each table alone before joining so i can catch any typo or errors in the query 

**GROUP BY vs ROW_NUMBER**
- GROUP BY does collapse and combines the over all transections to my rows
- ROW_NUMBER does bring all my rows together with same name one by one but wont combine them to my rows
- I'd use GROUP BY when i need over all spending or any final figure for a particular merchant , ROW_NUMBER when i want to keep them together by rank
