# `history()` 
- Fetch price data for one ticker from Yahoo and make user-friendly

## Parameters

| Parameter  | Description | Default | Valid values | 
| :--------: | :-------- | :------: | :-------- | 
| period: str | Either set period parameter or use start and end <br> Don't mix with start & end | '1mo' | 1d, 5d, 1mo, 3mo, 6mo, 1y, 2y, 5y, 10y, ytd, max |
| interval: str | Intraday data cannot extend last 60 days <br> * 1m - max 7 days within last 30 days <br> * up to 90m - max 60 days <br> * 60m, 1h - max 730 days (yes 1h is technically < 90m but this what Yahoo does)| '1d' | 1m,2m,5m,15m,30m,60m,90m,1h,1d,5d,1wk,1mo,3mo | 
| start: str | Download start date | '1900-01-01' (if period=None) | 'YYYY-MM-DD' string, _datetime, or epoch | 
| end: str,dt,int | Download end date | now (if period=None) | 'YYYY-MM-DD' string, _datetime, or epoch |
| prepost: bool | Include Pre and Post market data in results? | False |  |
| auto_adjust: bool | Dividend-adjust all OHLC automatically? | True |  |
| back_adjust: bool | Deprecated | False |  |
| repair: bool | Detect problems in price data and repair: <br> * very few prices = 0 or NaN <br> * volume=0 despite price movement <br> * very few prices 100x the rest | False ||
| keepna: bool | Keep NaN rows returned by Yahoo?  | False |  |
| proxy: str | Optional. Proxy server URL scheme. | None |  |
| rounding: bool | Optional. Round values using Yahoo-suggested precision? | False |  |
| timeout: float,None | Optional. Stop waiting for response after N seconds. | 10 |  |
| debug: bool | Print error messages? | True |  |
| raise_errors: bool | Raise errors as exceptions instead of printing? | False |  |

## Returns
Pandas DataFrame
