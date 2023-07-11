The new argument `repair=True` in `history()` and `download()` will attempt to fix a variety of price errors caused by Yahoo. Only US market data appears perfect, I guess Yahoo doesn't care much about rest of world?

The returned table will have a new column `Repaired?` that specifies if row was repaired.

# Missing dividend adjustment

If dividend in data but preceding `Adj Close` = `Close`, then manually apply dividend-adjustment to `Adj Close`.

Note: `Repaired?` is NOT set to `True` because fix only changes `Adj Close`

`8TRA.DE`

![image](https://github.com/ranaroussi/yfinance/assets/96923577/5b0bb171-1846-41cc-a115-353e33d77a06)

# Missing split adjustment

If stock split in data but preceding price data is not adjusted, then manually apply stock split.

Requires date range include 1 day after stock split, for calibration. Sometimes Yahoo fails to adjust prices on stock split day.

`MOB.ST`

![image](https://github.com/ranaroussi/yfinance/assets/96923577/02670df6-d14a-4cac-a5e6-462bc9e55d37)

# Missing data

If price data is clearly missing or corrupt, then reconstructed using smaller interval e.g. `1h` to fix `1d` data.

`1COV.DE` missing row

![image](https://github.com/ranaroussi/yfinance/assets/96923577/2032052a-11ab-4dca-8a7c-e99fcd3952a2)

`1COV.DE` missing Volume

![image](https://github.com/ranaroussi/yfinance/assets/96923577/39ed9634-d441-44a8-a4b7-0a1e186f5c0d)


# 100x errors

Sometimes Yahoo mixes up currencies e.g. $/cents or £/pence. So some prices are 100x wrong. 

Sometimes they are spread randomly through data - these detected with `scipy` module.

Other times they are in a block, because Yahoo decided one day to permanently switch currency.

`AET.L`

![image](https://github.com/ranaroussi/yfinance/assets/96923577/b669a76f-c0f0-4134-be0a-911d15a7c7a6)

# Price reconstruction - algorithm notes

Spam minimised by grouping fetches. Tries to be aware of data limits e.g. `1h` cannot be fetched beyond 2 years.

If Yahoo eventually does fix the bad data that required reconstruction, you will see it's slightly different to reconstructed prices and volume often significantly different. Best I can do, and beats missing data.
