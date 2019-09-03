---
layout: post
title: Cryptocurrency Correlations
cover: cover.jpg
date:   2019-09-02 18:40:00
categories: posts
---

## Asset correlations and diversification

  One of the major considerations for any investor is diversification - choosing multiple assets to invest in, in order to moderate risk. While this is broadly good practice, it's possible to overdiversify. You might imagine ranking a group of stocks by their expected performance, and then adding each to a portfolio, one by one. Each successive addition of a stock lowers the expected return and reduces the risk of the portfolio. At some point, the marginal benefit of the reduction in risk is washed out by the marginal cost of the reduction in expected return.
  
  For this reason, it's important to have a good idea of just how much you're getting for your dollar in the way of uncorrelated returns, rather than simply trusting your intuition in matters of diversification. No wisdom in overpaying, even when insuring against ruin.

## A quick note on Pearson and Spearman

  Most of the time the correlation coefficient you'll see used is Pearson's, which describes the linear relationship between two variables. If the relationship can be fitted perfectly to a line with positive slope, that's a 1. That said, there are other options. Most notable among them is Spearman's, which is no more than Pearson's correlation on the ranks of the data, rather than the data itself. The end result is a measurment that cares about the monotonicity of the relationship between the the two variables, rather than their relationship being perfectly linear. For example, the Pearson correlation of points which lie perfectly along a logistic curve is less than one - whereas the Spearman correlation will assign a one.
  
## On to the pretty pictures

{% include correlationchart.html %}
