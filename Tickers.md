# `download()`
Fetch price data for many tickers from Yahoo and make user-friendly.

## Interface
```python
yf.download(tickers, ...) -> pd.DataFrame
```

## Parameters
| Parameter  | Description | Default | Valid values | 
| :--------: | :-------- | :------: | :-------- | 
| tickers : str, list | List of tickers to download |  | E.g. "SPY AAPL MSFT", ["SPY", "AAPL", "MSFT"] |
| period: str | Either set period parameter or use start and end <br> Don't mix with start & end | 'max' | 1d, 5d, 1mo, 3mo, 6mo, 1y, 2y, 5y, 10y, ytd, max |
| interval: str | Intraday data cannot extend last 60 days <br> * 1m - max 7 days within last 30 days <br> * up to 90m - max 60 days <br> * 60m, 1h - max 730 days (yes 1h is technically < 90m but this what Yahoo does)| '1d' | 1m,2m,5m,15m,30m,60m,90m,1h,1d,5d,1wk,1mo,3mo | 
| start: str | Download start date, inclusive | '1900-01-01' (if period=None) | 'YYYY-MM-DD' string, _datetime, or epoch | 
| end: str,dt,int | Download end date, exclusive | now (if period=None) | 'YYYY-MM-DD' string, _datetime, or epoch |
| prepost: bool | Include Pre and Post market data in results? | False |  |
| auto_adjust: bool | Dividend-adjust all OHLC automatically? | False |  |
| back_adjust: bool | Deprecated | False |  |
| repair: bool | Detect problems in price data and repair: <br> * very few prices = 0 or NaN <br> * volume=0 despite price movement <br> * very few prices 100x the rest | False ||
| keepna: bool | Keep NaN rows returned by Yahoo?  | False |  |
| rounding: bool | Optional. Round values using Yahoo-suggested precision? | False |  |
| group_by : str | Group by 'ticker' or 'column' | 'column' |  |
| ignore_tz : bool | When aligning data from different exchanges, ignore different timezones? | True | |
| threads : bool, int | How many threads to use for mass downloading. <br> If True, number of threads = CPUs * 2 | True | |
| proxy: str | Optional. Proxy server URL scheme. | None |  |
| timeout: float,None | Optional. Stop waiting for response after N seconds. | 10 |  |
| progress : bool | Print progress bar. | True |  |

## Returns
Pandas DataFrame