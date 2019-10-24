---
layout: post
title: Animal Spirits
cover: cover.jpg
date:   2019-10-23 22:40:00
categories: posts
---



## The abstract


  Sentiment analysis is a valuable tool for determining when the value of an asset is caught in a feedback loop, which can help with evading bad investment decisions, or allow you to make high-payoff contrarian trades. This is especially true of cryptocurrency markets, where there's not much fundamental information to be had and what's there is publicly available.
  
Sentiment analysis of tweets in the bitcoin hashtag provides some interesting results - while a lot of the most predictive words are simply expressions of positive or negative feeling, as you'd expect, some are quite specific - like "SEC". While that's not necessarily unexpected, it provides some real justification for using tools that are trained on the specific context of use for sentiment analysis, rather than simply using a general sentiment analysis library.


<img src="\images\positive_importance_chart.png">

<img src="\images\neutral_importance_chart.png">

<img src="\images\negative_importance_chart.png">


We can also look at the Shapley values for a specific prediction to see how the model made it's choice regarding the tweet. Red indicates pushing in favor of the predicted class, blue against it. These are fake tweets I'm putting into the model; I've intentionally avoided using words with obvious sentiment.

"bitcoin is a tool for liberation posing as a get-rich-quick scheme"



"bitcoin is a distributed ledger with no net moral valence"



"bitcoin is a ponzi scheme and SEC intervention is on its way"




# Into the weeds

## Bulls, bears, and beauty contests

What does it mean to make money in an asset market? The necessary and sufficient condition for executing a successful trade is that it anticipates the future price of some asset to some degree of specificity. There are many ways one might go about anticipating the future price of an asset. If it's a stock, you could look at earnings reports and balance sheets to compare its book value and cashflow to its price. Similar principles apply to bonds, interest rates, and default risk; or commodities, supply, and demand.


But markets are multi-agent systems; other players generally have access to the same information you do. A bet on a given asset rising in price is a bet that everyone else who has taken up the opposite side of the bet is wrong - that they have failed to take into account some source of information, or failed to interpret that information properly. If you're an individual retail investor, that tends to be a poor bet to make - if you don't spend a few hours every day on a Bloomberg Terminal, it's better to assume either informational equilibrium or some disadvantage on your part.


So if the general assumption is informational equilibrium, what then drives market movements other than the propagation of this information through the market? Markets are multi-agent systems; if you and the other players have access to the same information, the main item to concern yourself with is *how you anticipate other players will price the asset.* If other players will price the stock higher in the future, it pays to own it. And if you're prepared to own it due to an expectation that other players will price it higher in the future, it pays for *others* to own it!


See the feedback loop? This is a Keynesian beauty contest - a scenario where the winning play is not a faithful expression of your own beliefs but rather anticipation of the beliefs of others. It's implicated in bubble formulation and the amplification of random noise in asset markets - but the cash value (hah!) of any hypothesis about the market is what extent you can make money with it.


If the relevant information about a given asset has already been priced in, and sentiment is still extremely negative, this suggests that purchasing the asset is a *good idea*. Why? If all information has been accounted for in the price, sentiment should be *neutral* - the price has already declined to account for all the negative information. Therefore, the sentiment is irrational and it's eventual correction will cause the price to increase. Similar reasoning can be applied in reverse.


This makes sentiment indicators a valuable trading tool. If the the magnitude of the sentiment regarding the asset is outsized compared to information about the actual asset, or if you think the information has already been taken into account and the sentiment hasn't leveled out, trading against it makes you money.

  
## Why bitcoin?

Bitcoin does not have earnings reports or balance sheets; it's inflation rate is set programmatically and can be anticipated near perfectly. This is largely true for other cryptocurrencies as well - the closest thing they're liable to have is money in the coffers for the foundations that fund their development, and the behavior of their developers and promoters. Much of the information that could be gleaned about a cryptocurrency, things like transaction volume, or number of unique chain validators, even things like the health of the network, can be pulled directly either from the protocol itself or from one of the many publicly available block explorer APIs. There's not a huge amount of information to be had, and what is, is readily available. Sentiment should therefore be a substantial driver, given how easy it is to incorporate other information.

## The model

 The dataset consists of about 50,000 tweets, all collected on March 23rd, 2018, and a sentiment score - negative, neutral or positive. The tweets were unprocessed - raw text, with their links and usernames still included. I cleaned out links, usernames, strange characters and the like with regex, and then used spaCy's language model and a bag-of-words vectorizer from scikit-learn to tokenize and vectorize the tweet, removing all punctuation and "stop words" - words which lack contextual value, like "the" or "and". This was followed by SelectKBest to keep the 2000 most correlated words. The resulting dataset consisted of the number of occurences of each of those 2000 words in each tweet.
 
 
This was then passed into a linear support vector classifier - SVMs are notable for being able to handle high dimensionality quite well. The model achieved a fivefold cross-validation accuracy of 93.2 percent, and 93.1 percent on the holdout. For reference, the majority class was positive at 45.1 percent.


I also pulled a set of 1000 tweets with the bitcoin hashtag using TweePy, and made two versions of the same set - one where sentiment was autoscored with the TextBlob library, and then another where I scored them by hand. Both of them had the same classes; negative, neutral, and positive. The accuracy was substantially reduced for both - the autoscored version at 78.4 percent and the hand-scored version at 66.5 percent. This suggests a tight scope to the context of sentiment analysis - tweets at different times, scored by different people, and/or using a more general model of sentiment scoring produce drastically different results.
Here you can see the class precisions for the holdout set, the autoscored set, and the hand-scored set.

<img src="\images\class_fscores_chart.png">
