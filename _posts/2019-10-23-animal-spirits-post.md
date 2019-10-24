---
layout: post
title: Animal Spirits
cover: cover.jpg
date:   2019-10-23 22:40:00
categories: posts
---



# The abstract


  Sentiment analysis is a valuable tool for determining when the value of an asset is caught in a feedback loop, which can help with evading bad investment decisions, or allow you to make high-payoff contrarian trades. This is especially true of cryptocurrency markets, where there's not much fundamental information to be had and what's there is publicly available.
  
Sentiment analysis of tweets in the bitcoin hashtag provides some interesting results - while a lot of the most predictive words are simply expressions of positive or negative feeling, as you'd expect, some are quite specific - like "SEC". While that's not necessarily unexpected, it provides some real justification for using tools that are trained on the specific context of use for sentiment analysis, rather than simply using a general sentiment analysis library.

Below are charts displaying the importance of words in classifying tweets as positive, neutral, or negative relative to bitcoin. Mouse over the bar to see it's exact value.


{% include positive_importance_chart.html neutral_importance_chart.html negative_importance_chart.html %}



{% include neutral_importance_chart.html %}

{% include negative_importance_chart.html %}






We can also look at the Shapley values for a specific prediction to see how the model made it's choice regarding the tweet. Red indicates pushing in favor of the predicted class, blue against it. These are fake tweets I'm putting into the model; I've intentionally avoided using words with obvious sentiment.
(shapley charts here)


# Into the weeds
## A quick note on Pearson and Spearman

  Most of the time the correlation coefficient you'll see used is Pearson's, which describes the linear relationship between two variables. If the relationship can be fitted perfectly to a line with positive slope, that's a 1. That said, there are other options. Most notable among them is Spearman's, which is no more than Pearson's correlation on the ranks of the data, rather than the data itself. The end result is a measurment that cares about the monotonicity of the relationship between the the two variables, rather than their relationship being perfectly linear. For example, the Pearson correlation of points which lie perfectly along a logistic curve is less than one - whereas the Spearman correlation will assign a one.
  
## On to the pretty pictures

## What did we learn?

  Investment managers generally consider correlations below 0.8 to be insignificant - this puts quite a few of these assets below the bar of correlation. In fact, every option other than Ethereum is uncorrelated with Bitcoin. Granted, some of this can be attributed to the general volatility of cryptoassets at the moment - if it's a random walk on Wall Street, maybe it's a random rush around the block(chain).

  Some of these correlations throw my intuitions a bit. I wasn't expecting Tether to be so uncorrelated - while the price is pegged to a dollar, I used marketcaps here precisely so that the value of the broader asset would be reflected, and less influenced by issuance schemes. Tether's marketcap can be thought of as being the amount of US dollars Tether holds in reserve to back the token, modulo for the market's broader confidence in them. There have been some crises of confidence in Tether recently, and it is reasonable to think that the inflow and outflow from Tether's coffers might be quite different from the net value of Bitcoin.
  
  Other interesting items - Ethereum is more correlated to Bitcoin than Litecoin, despite Litecoin being a Bitcoin clone. The major differences Litecoin has relative to Bitcoin are a shorter block time, greater total supply and a hashing algorithm which lets CPUs and GPUs perform slightly better compared to ASICs. Ethereum is fundamentally different in that it allows for smart contracts, which dramatically expand the space of what can be done with the protocol. Binancecoin, which is largely just a medium of exchange on one of the larger exchanges, and Bitcoin Cash SV, a recent Bitcoin fork, are the least correlated other than Tether, perhaps because they both are twinned a little more closely to confidence in some individual or institution.
  
  Dramatic as ever in the cryptocurrency space, I suppose.
  
  *Data pulled from Coingecko's [API](https://www.coingecko.com/en/api) - it's free and doesn't require a key.*
