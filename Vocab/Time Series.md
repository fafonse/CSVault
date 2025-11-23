Time series data is one variable that has dates/time, and another has a continuous outcome.
> EX: Flu deaths per year, monthly sales, hourly temperature
- Sequence of data points recorded over time
	- Usually at regular intervals

There are 4 components of a *time series*.
1. Trend
	- Long term increase or decrease
	- EX: Sales over the years
2. Seasonality
	- Repeating pattern (fixed period)
	- EX: Ice cream sales peak in summer
3. Cyclical
	- Repeating increase then decrease (or vice versa)
	- Economy boom and bust
4. Random/Noise
	- Unpredictable fluctuations
	- Random daily errors

## Models

**Additive model**: $Y = T + S + C + R$
**Multiplicative**: $Y = T * S * C * R$ (common when variance grows)


## Stationarity

The most important concept. Most models ([[ARIMA]], etc.) only work on *stationary data*.

A series is stationary if...
- [[Measures of Center|Mean]] is constant over time
- [[Standard Deviation|Variance]] is constant over time
- No trend or seasonality
> Basically your trend line is stationary if it's trendline is a flat line

There are a couple methods to check:
- Look at plot
- Rolling mean and STD
- ADF test ($p  < 0.05 \rightarrow$ stationary)

### Making Data Stationary
Common Fixes:
1. Log transformation $\rightarrow$ stabilizes variance
2. Differencing $\rightarrow$ subtract previous value
	- `diff = series - series.shift(1)`
	- Keep finding the differences until the data is stationary
3. Detrending $\rightarrow$ subtract previous value
4. Seasonal differencing (subtract value from 12 months ago)
	- If there's seasonality, you can take the differences from "seasons" ago

Usually 1 or 2 differences are enough (d = 1 or 2 in [[ARIMA]])