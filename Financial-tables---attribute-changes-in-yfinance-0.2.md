Purpose:
This page is an attempt to assist other yfinance users that come across 'backward compatibility' issues due to some financial attributes that either changed names or were moved to other tables, due to changes made by yahoo.

<feel free to add / update, as applicable>

* quarterly_financials.loc['Total Stockholder Equity']  ==> quarterly_balancesheet.loc['Stockholders Equity']

Other changes in quarterly_balancesheet:
* 'Cash' -> 'Cash And Cash Equivalents'
* 'Total Liab' -> 'Total Liabilities Net Minority Interest'
* 'Short Term Investments'-> 'Other Short Term Investments'

Changes in quarterly_cashflow:
* quarterly_cashflow.loc['Capital Expenditures'] ==> 'Capital Expenditure'
* quarterly_cashflow.loc['Total Cash From Operating Activities'] ==> 'Cash Flow From Continuing Operating Activities'
