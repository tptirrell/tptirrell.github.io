---
layout: post
title: Beating the Stock Market?
---

**Objective**: To produce a list of ETF trades based on general market buy/sell indicators from 2010-2016, explore these trades to find any trends/correlations, and ultimately classify those that will yield a profit from those that will not.

My motivation behind this project can be seen in the graphic below which shows the S&P500 for the year 2015. Even though, the year as a whole was flat, there was a shift of at least 2% in either direction 25 times. I want to know if it's possible to capitalize on those shifts.

![functions](/images/Market/1.jpg)

**The Data:**
I decided to focus on ETFs for this analysis and used the 100 most traded ETFs for each year as a starting point. Then, to generate a list of trades for the dataset, I used a measure of the ETFs momentum (Relative Strength Index or RSI) as a signal to buy/sell and short/cover.

This produced a list of 3270 trades that would have been made since 2010. The mean return on these trades is 0.58% for short trades and 1.8% for regular trades. The mean holding times (ie the difference between the signal to buy and the signal to sell) is 18 days and 30 days for short and regular trades, respectively. The ratio of short trades to regular trades was approximately 2:1.

Exploring the data a bit, I found something very interesting. The below plots show each trade over the 6.5 years (x-axis) against the percent return (y-axis) -- the regular trades in blue and the short trades in red. The size of the bubble represents the length of time the position was held. There is a very clear distinction with regard to trade length above and below the black line at 0%. This does not mean that you should sell at a magic number of days and always turn a profit. It does, however, mean that when the signals to buy and sell worked correctly (meaning positive return), they worked quickly.

![functions](/images/Market/2a.png)
![functions](/images/Market/3a.png)

If we then look at the length of time that each trade was held against the return percentage, we can again see the trend of trades that were held longer, were far more likely to be negative. Interestingly, every trade that signaled to buy and sell in under 10 days had a positive return.

![functions](/images/Market/4.jpg)

So this provides a good starting point for our model. Since we have a perfect record at 10 days, is it possible to classify the remaining trades into those that eventually return a profit from those that do not. Cutting your losses on the losing trades will free up capital to reinvest.

**Model Building:**
Before running the models, it's important to note that the baseline is 58% -- meaning 58% of the trades remaining at 10 days will eventually end in a profit.

Using the ETF moving averages(20, 50, 100, and 200 day), volatility, RSI, one week performance, and overall market volatility as features, I ran the following classification models training on data from 2010-2013 and testing on 2014-2016. The associated accuracy score is listed with each model.

![functions](/images/Market/5.png)

So, the models are actually able to classify the trades we should keep from the ones we should drop with approximately 70% accuracy. However, since some trades yield a higher profit than others, a simple accuracy score is not enough to say that we have made an improvement. After simulating each of these classifications, the baseline still provides a higher annualized return.

**Back to square one...**
I looked at every feature and if there was anything else that I was missing. I noticed a slight variation in the moving averages between the trades that were profitable and not. The below histogram shows the difference between the 20 and 50 day moving averages relative to the 20 day moving average. Turns out, there is a clear difference in this ratio between the trades we want to keep and the one want to drop, and if we keep all trades with a ratio less than 0.0035, we will keep 79.3% of the trades we want and only 14.1% of those we don't.

![functions](/images/Market/6.png)

**Results:**
Using the RSI as a buy/sell indicator and the above ratio of moving averages as a classification point, I was able to outperform the stock market from 2014-2016 by 1.7% annually.


**Next Steps:**
There are areas for improvement and further analysis within this project. A few first steps are:

- Use Time Series to find ideal buy/sell signals. Right now, I am using only RSI as a static indicator.
- Investigate expanding to more than 100 ETFs (and with no commission fees). This will hopefully allow for slightly better classification. Also, commission fees were not taken into consideration which will dramatically affect the final return percentage.
- Identify a more dynamic "cutoff" period. Using 10 days across the board is certainly not ideal.
- Finally, watch the model performance in real time for 3 months to see actual returns.
