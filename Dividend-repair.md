Fix errors in dividends:

1. adjustment missing, or 100x too small/big for the dividend
2. duplicate dividend (usually within days)
3. dividend 100x too big/small for the ex-dividend price drop

Almost all errors I've seen are on London stock exchange (£/pence mixup), but no exchange is safe.

Because (3) relies on price action, detection is best with 1d intervals, basically perfect. Accuracy worsens with longer intervals - 1wk, 1mo - and also false positive rate is higher. So for accurate adjusted 1wk/1mo prices, first fetch 1d adjusted prices and resample to 1wk/1mo:

```python
df = dat.history(interval='1d', auto_adjust=True, ...)
df.loc[df['Stock Splits']==0.0, 'Stock Splits'] = 1.0
df_wk = df.resample('W').agg({
    'Open': 'first', 'Low': 'min', 'High': 'max', 'Close': 'last',
    'Volume': 'sum', 'Dividends': 'sum', 'Stock Splits': 'prod',
    'Repaired?': 'any'
    })
df_wk.loc[df_wk['Stock Splits']==1.0, 'Stock Splits'] = 0.0
```