Fix errors in dividends:

1. adjustment missing, or 100x too small/big for the dividend
2. duplicate dividend (within 7 days)
3. dividend 100x too big/small for the ex-dividend price drop

Almost all errors I've seen are on London stock exchange (£/pence mixup), but no exchange is safe.

----

### IMPORTANT

Because fixing (3) relies on price action, there is a chance of a "false positive" (FP) - thinking an error exists when data is good.
FP rate increases with longer intervals, so only 1d intervals are repaired. If you request repair on multiday intervals (weekly etc), then: 1d is fetched from Yahoo, repaired, then resampled.

FP rate on 1d is tiny. They tend to happen with tiny dividends e.g. 0.5%, mistaking normal price volatility for an ex-div drop 100x bigger than the dividend, causing repair of the "too small" dividend. Either accept the risk, or fetch 1-2 years of prices with at least 3 dividends - then can analyse the dividends together to identify false positives.

----

### Examples

#### Duplicate

> ALC.SW

```
# ORIGINAL:
                               Close  Adj Close  Dividends
2023-05-10 00:00:00+02:00  70.580002  70.352142       0.21
2023-05-09 00:00:00+02:00  65.739998  65.318443       0.21
2023-05-08 00:00:00+02:00  66.379997  65.745682       0.00
```
```
# REPAIRED:
                               Close  Adj Close  Dividends
2023-05-10 00:00:00+02:00  70.580002  70.352142       0.00
2023-05-09 00:00:00+02:00  65.739998  65.527764       0.21
2023-05-08 00:00:00+02:00  66.379997  65.956371       0.00
```

#### Dividend too big

> HLCL.L

```
# ORIGINAL:
                           Close  Adj Close     Adj  Dividends
2024-06-27 00:00:00+01:00  2.360     2.3600  1.0000       1.78
2024-06-26 00:00:00+01:00  2.375     2.3572  0.9925       0.00

# REPAIRED:
                           Close  Adj Close     Adj  Dividends
2024-06-27 00:00:00+01:00  2.360     2.3600  1.0000     0.0178
2024-06-26 00:00:00+01:00  2.375     2.3572  0.9925     0.0000
```

#### Dividend too small

> BVT.L

```
# ORIGINAL:
                            Close  Adj Close     Adj  Dividends
2022-02-03 00:00:00+00:00  0.7534   0.675197  0.8962    0.00001
2022-02-01 00:00:00+00:00  0.7844   0.702970  0.8962    0.00000
```
```
# REPAIRED:
                            Close  Adj Close     Adj  Dividends
2022-02-03 00:00:00+00:00  0.7534   0.675197  0.8962      0.001
2022-02-01 00:00:00+00:00  0.7844   0.702075  0.8950      0.000
```

#### Adjusted 2x on day before (clue: Close < Low)

> 2020.OL

```
# ORIGINAL:
                                  Low       Close   Adj Close  Dividends
2023-12-21 00:00:00+01:00  120.199997  121.099998  118.868782       0.18
2023-12-20 00:00:00+01:00  122.000000  121.900002  119.477371       0.00
```

```
# REPAIRED:
                                  Low       Close   Adj Close  Dividends
2023-12-21 00:00:00+01:00  120.199997  121.099998  118.868782       0.18
2023-12-20 00:00:00+01:00  122.000000  122.080002  119.654045       0.00
```