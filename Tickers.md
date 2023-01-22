# `download()`
- descriptions
Fetch price data for many tickers from Yahoo and make user-friendly.
- interface
```python
download(self, period, interval, start, end, prepost, actions, auto_adjust, repair, proxy, threads, group_by, progress, timeout, **kwargs) -> Any
```
- parameters

Most parameters are identical to [`Ticker.history`](https://github.com/ranaroussi/yfinance/wiki/TickerBase#history).  
Differences: 

| parameters | description | default value | valid value | 
| :--------: | :-------- | :------: | :-------- | 
| period : str | | 'max' | |
| auto_adjust: bool |  | False |  |
| show_errors : bool | Rename of 'debug'. | False |  |

New parameters: 

| parameters | description | default value | valid value | 
| :--------: | :-------- | :------: | :-------- | 
| tickers : str, list | List of tickers to download |  | |
| threads : bool, int | How many threads to use for mass downloading. <br> If True, number of threads = CPUs * 2 | True | |
| ignore_tz : bool | When aligning data from different exchanges, ignore different timezones? | False | |
| group_by : str | | 'column' | Group by 'ticker' or 'column' |
| progress : bool | Print progress bar. | True |  |