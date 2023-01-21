Purpose:
This page is an attempt to assist other yfinance users that come across 'backward compatibility' issues due to some financial attributes that either changed names or were moved to other tables, due to changes made by yahoo.

### quarterly_financials
* 'Total Stockholder Equity' -> 'Stockholders Equity' and moved to `quarterly_balancesheet`

### quarterly_balancesheet:
* 'Cash' -> 'Cash And Cash Equivalents'
* 'Total Liab' -> 'Total Liabilities Net Minority Interest'
* 'Short Term Investments'-> 'Other Short Term Investments'

### quarterly_cashflow:
* 'Capital Expenditures' -> 'Capital Expenditure'
* 'Total Cash From Operating Activities' -> 'Cash Flow From Continuing Operating Activities'
