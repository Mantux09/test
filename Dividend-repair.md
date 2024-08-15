Fix errors in dividends:

1. adjustment missing, or 100x too small/big for the dividend
2. duplicate dividend (usually within days)
3. dividend 100x too big/small for the ex-dividend price drop

Almost all errors I've seen are on London stock exchange (£/pence mixup), but no exchange is safe.

Because (3) relies on price action, detection is best with 1d intervals and worsens with longer intervals (1wk, 1mo).