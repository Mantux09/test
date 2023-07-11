# `history()` 

Fetch price data for one ticker from Yahoo and make user-friendly.

## Interface
```python
yf.Ticker(symbol).history(...) -> pd.DataFrame
```

## Parameters

| Parameter  | Description | Default | Valid values | 
| :--------: | :-------- | :------: | :-------- | 
| interval: str | Limits on intraday data: <br> • `1m` = max 7 days within last 30 days <br> • `60m`, `1h` = max 730 days <br> • else up to `90m` = max 60 days| '1d' | 1m, 2m, 5m, 15m, 30m, 60m, 90m, 1h,<br>1d, 5d, 1wk, 1mo, 3mo |
| period: str | Range duration. Don't mix with `start` or `end` | '1mo' | 1d, 5d, 1mo, 3mo, 6mo,<br>1y, 2y, 5y, 10y, ytd, max | 
| start: str,dt,int | Range start, inclusive | '1900-01-01' (if period=None) | 'YYYY-MM-DD', datetime, or epoch | 
| end: str,dt,int | Range end, exclusive | now (if period=None) | 'YYYY-MM-DD', datetime, or epoch |
| prepost: bool | Include Pre and Post market data in results? | False |  |
| auto_adjust: bool | Dividend-adjust all OHLC automatically? | True |  |
| back_adjust: bool | Deprecated | False |  |
| repair: bool | Detect problems in price data and repair. [See Wiki page for details](https://github.com/ranaroussi/yfinance/wiki/Price-repair) | False |  |
| keepna: bool | Keep NaN rows returned by Yahoo?  | False |  |
| proxy: str | Optional. Proxy server URL scheme. | None |  |
| rounding: bool | Optional. Round values using Yahoo-suggested precision? | False |  |
| timeout: float,None | Optional. Stop waiting for response after N seconds. | 10 |  |
| raise_errors: bool | Raise errors as exceptions instead of printing? | False |  |

## Returns
Pandas DataFrame
