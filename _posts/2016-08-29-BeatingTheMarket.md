---
layout: post
title: Beating the Stock Market?
---

**Objective**: To produce a list of ETF trades based on general market buy/sell indicators from 2010-2016, explore the data to find any trends/correlations and ultimately determine if classification is possible of trades that yielded a profit from those that did not.

My motivation behind this project can be seen in the graphic below which shows the S&P500 for the year 2015. Even though, the year as a whole was flat, there was a shift of at least 2% in either direction 25 times. I want to know if it's possible to capitalize on those shifts.

![functions](/images/Market/1.png)

**The Data**
I decided to focus on ETFs for this analysis and used the 100 most traded ETFs for each year as a starting point. Then, to generate a list of trades for the dataset, I used a measure of the ETFs momentum (Relative Strength Index or RSI) as a signal to buy/sell and short/cover.

This produced a list of 3270 trades that would have been made since 2010. The mean return on these trades is 0.58% for short trades and 1.8% for regular trades. The mean holding times (ie the differene between the signal to buy and the signal to sell) is 18 days and 30 days for short and regular trades, respectively. The ratio of short trades to regular trades was approximately 2:1.

Exploring the data a bit, I found something very interesting. The below plots show each trade over the 6.5 years (x-axis) against the percent return (y-axis) -- the regular trades in blue and the short trades in red. The size of the bubble represents the length of time the position was held. There is a very clear distinction with regard to trade length above and below the black line at 0%. This does not mean that you should sell at a magic number of days and always turn a profit. It does, however, mean that when the signals to buy and sell worked correctly (meaning positive return), they worked quickly.

![functions](/images/Market/2a.png)
![functions](/images/Market/3a.png)

If we then look at the length of time that each trade was held against the return percentage, we can again see the trend of trades that were held longer, were far more likely to be negative. Interestingly, every trade that signaled to buy and sell in under 10 days had a positive return.

![functions](/images/Market/4.png)

So this provides a good starting point for our model. Since we have a perfect record at 10 days, is it possible to classify the remaining trades into those that eventually return a profit from those that do not. Cutting your losses from the losing trades will free up capital to reinvest.

***Model Building***


![functions](/images/Movies/8.png)

The three most important features are, not suprisingly, number of votes, movie runtime, and year released for reasons laid out above.

![functions](/images/Movies/7.png)

Finally, we can graph the predicted ratings from the GB model against the actual ratings from the test set to visualize model performance. We can see the model
predicts rather well but with more errors at the high and low end of the dataset with respect to rating. This is most likely due to less data
available in these ranges.

![functions](/images/Movies/9.png)

**Next Steps:**

While this model is a great start in predicting ratings, there are a few areas for improvement that should be explored.

- Additional data should be obtained with ratings at the extremes, especially higher rated movies.
- This model does not take into account actors, writers, or directors. These can absolutely influence a movie's rating.
- Pulling data from additional ratings websites should be considered. While IMDb may be the most popular, it certainly isn't the only one.
