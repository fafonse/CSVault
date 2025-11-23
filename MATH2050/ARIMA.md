## Parameters

**AR**
- Parameter $q$
	- Needs to be guessed
**I**:
- Parameter $d$

**[[Moving Average|MA]]**: e
- Parameters $q$
	- Needs to be guessed

### Guessing your parameters

- ACF (Autocorrelation Function)
	- Shows correlation with past lags
	- Helps identify $q$ order
	- A sine pattern shows seasonality in the model
		- Find the time period of the seasonality (time lag)
	- The peak is your $q$
- *PACF (Partial Autocorrelation)**
	- Correlation after removing earlier effects
	- Helps identify $p$ order
	- Removes the correlation from earlier data except for the immediate one before the current
		- EX: In a family, it shows your correlation to your dad, while removing all the correlation/effects of your heritage from your grandpa and up.

Quick rules for stationary data:
- ACF cuts off after lag $q \rightarrow$ find [[Moving Average|MA]] of $q$
- PACF cuts off after lag $p \rightarrow$ find AR of $p$
- Both decay slowly $\rightarrow$ need differencing