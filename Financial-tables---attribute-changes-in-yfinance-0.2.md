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

### additional attributes that changed once moving to 0.2.7:
* Ticker.info['marketCap'] -> Ticker.fast_info['market_cap']
* Ticker.info['fiftyTwoWeekLow'] -> Ticker.fast_info['year_low']
* Ticker.info['fiftyTwoWeekHigh'] -> Ticker.fast_info['year_high']
* Ticker.info['regularMarketPreviousClose'] -> Ticker.fast_info['previous_close']
* Ticker.info['52WeekChange'] -> Ticker.fast_info['year_change']
* Ticker.info['averageVolume10days'] -> Ticker.fast_info['ten_day_average_volume']
* Ticker.info['averageVolume'] -> Ticker.fast_info['three_month_average_volume']
* Ticker.info['fiftyDayAverage'] -> Ticker.fast_info['fifty_day_average']
* Ticker.info['twoHundredDayAverage'] -> Ticker.fast_info['two_hundred_day_average']
* # need to call Ticker.history(period='1d') first in order to get access to history_metadata
* Ticker.info['regularMarketPrice'] -> Ticker.history_metadata['two_hundred_day_average'] 
