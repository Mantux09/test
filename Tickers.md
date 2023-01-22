# `download()` (WIP: this method is in `Tickers` class)
- descriptions
Fetch price data for many tickers from Yahoo and make user-friendly.
- interface

- parameters
### Parameters

Most parameters are identical to `Ticker.history`. Differences:

#### Different parameters

##### period
Default = max

##### auto_adjust
Default = False

##### show_errors
Rename of 'debug'. Default = False

#### New parameters:

##### tickers
str, list

List of tickers to download

##### threads
bool, int

How many threads to use for mass downloading. Default = True.

If True, number of threads = CPUs * 2

##### ignore_tz
bool

When aligning data from different exchanges, ignore different timezones? Default = False

##### group_by
str

Group by 'ticker' or 'column' (default)

##### progress
bool

Print progress bar. Default = True