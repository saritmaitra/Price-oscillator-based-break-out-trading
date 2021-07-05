# Absolute_Price_Oscillator

Here, I have experimented with a trading strategy that adjusts for trading instrument volatility.

An intuitive way to think is that as price volatility goes up, because prices make bigger swings at faster paces, our confidence in terms of investment drops. Conversely, as price volatility goes down, we are more willing to have bigger positions and hold those positions for longer periods of time. 

Here, I have applied volatility measures to trading strategies. Momentum strategies can use changing volatility to dynamically change the time period parameters used in the moving averages, or change the thresholds for how many up/down days to count as an entry signal. Another area of improvement would be using changing volatility to dynamically adjust thresholds on when to enter a position when a trend is detected, and dynamically adjust thresholds on when to exit a position when trend reversal is detected.

We can use dynamically changing time periods for moving averages, and dynamically changing thresholds for entering positions when overbuying and overselling is detected, or
dynamically changing thresholds for exiting positions when reversal to equilibrium prices are detected.

## Mean reversion strategy using the APO trading signal
This is an experimentation; so no emas are taken arbitarily. It will use a static constant of 10 days for the Fast EMA and a static constant of 40 days for the Slow EMA. It will perform buy trades when the APO signal value drops below -10 and perform sell trades when the APO signal value goes above +10. In addition, it will check that new trades are made at prices that are different from the last trade price to prevent overtrading. Positions are closed when the APO signal value changes sign, that is, close short positions when APO goes negative and close long positions when APO goes positive.

In addition, positions are also closed if currently open positions are profitable above a certain amount, regardless of APO values. This is used to algorithmically lock profits and initiate more positions instead of relying only on the trading signal value.

## Trend-following strategy using APO trading signal
Similar to the mean reversion strategy, a trend-following strategy can be built that uses the APO trading signal. The only difference here is that we enter long positions
when the APO is above a certain value, expecting price moves to continue in that direction, and we enter short positions when the APO is below a certain value, expecting price moves to continue going down. I have used STDEV as a measure of volatility and adjust the trend-following strategy to adapt to changing market volatility. This is almost an identical approach like adjusting the mean reversion trading strategy for market volatility.
