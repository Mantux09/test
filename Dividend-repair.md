Fix errors in dividends:

1. adjustment missing, or 100x too small/big for the dividend
2. duplicate dividend (within 7 days)
3. dividend 100x too big/small for the ex-dividend price drop

Almost all errors I've seen are on London stock exchange (£/pence mixup), but no exchange is safe.

----

### IMPORTANT

Because fixing (3) relies on price action, there is a chance of a "false positive" (FP) - thinking an error exists when data is good.
FP rate increases with longer intervals, so only 1d intervals are repaired. If you request repair on multiday intervals (weekly etc), then: 1d is fetched from Yahoo, repaired, then resampled.

FP rate on 1d is tiny. They tend to happen with tiny dividends e.g. 0.5%, mistaking normal price volatility for an ex-div drop 100x bigger than the dividend, and repairing the "too small" dividend. Either accept the risk, or fetch 1-2 years of prices with at least 3 dividends - then can analyse the dividends together to identify false positives.

----

