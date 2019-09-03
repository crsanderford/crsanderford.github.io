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

## What did we learn?

  Investment managers generally consider correlations below 0.8 to be insignificant - this puts quite a few of these assets below the bar of correlation. In fact, every option other than Ethereum is uncorrelated with Bitcoin. Granted, some of this can be attributed to the general volatility of cryptoassets at the moment - if it's a random walk on Wall Street, maybe it's a random rush around the block(chain).

  Some of these correlations throw my intuitions a bit. I wasn't expecting Tether to be so uncorrelated - while the price is pegged to a dollar, I used marketcaps here precisely so that the value of the broader asset would be reflected, and less influenced by issuance schemes. Tether's marketcap can be thought of as being the amount of US dollars Tether holds in reserve to back the token, modulo for the market's broader confidence in them. There have been some crises of confidence in Tether recently, and it is reasonable to think that the inflow and outflow from Tether's coffers might be quite different from the net value of Bitcoin.
  
  Other interesting items - Ethereum is more correlated to Bitcoin than Litecoin, despite Litecoin being a Bitcoin clone. The major differences Litecoin has relative to Bitcoin are a shorter block time, greater total supply and a hashing algorithm which lets CPUs and GPUs perform slightly better compared to ASICs. Ethereum is fundamentally different in that it allows for smart contracts, which dramatically expand the space of what can be done with the protocol. Binancecoin, which is largely just a medium of exchange on one of the larger exchanges, and Bitcoin Cash SV, a recent Bitcoin fork, are the least correlated other than Tether, perhaps because they both are twinned a little more closely to confidence in some individual or institution.
  
  Dramatic as ever in the cryptocurrency space, I suppose.
  
  *Data pulled from Coingecko's [API](https://www.coingecko.com/en/api) - it's free and doesn't require a key.*
