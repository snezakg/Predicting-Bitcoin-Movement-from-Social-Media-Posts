# Predicting-Bitcoin-Movement-from-Social-Media-Posts

This project aims at predicting long and short terms movements of the Bitcoin price by analysing the Twitter and Reddit posts related to Bitcoin.

## Method summary

Bitcoin price history is retrieved from Yahoo! finance. The dataset covers about 1 year of data with daily frequency.

Features used in this project can be divided in several categories:
- post statistics, such as number of likes, repostings, quotes, comments etc,
- sentiment extracted from the posts,
- activity of social media influencers,
- daily distribution of topics in the posts,
- bitcoin price in the previous period.

Sentiment is extracted using Vader sentiment analyser. Influencers are identified as a few individuals creating a lot of response. Topics are identified using LDA method. The features describing the previous period are comuted as rolling average and standard deviation of 10/5/3/2 previous days. All features are aggregated to a daily frequency.

Modelling of the movement is approached in two ways:
- modelling future quantities using a regressor, and
- forcasting using time series analysis.

The former is performed by predicting several features regarding the Bitcoin price on the following day using an XGBoost regressor. Features modelled comprice:
- the Bitcoin price of the following day,
- the absolute difference between the Bitcoin prices on the following and the actual day,
- the relative difference between the Bitcoin prices on the following and the actual day,
- the sign of the difference between the Bitcoin prices on the following and the actual day (i.e. the information whether the Pitcoin price rises or drops on the following day). This one is modelled using an XBGoost classifier.

The time series forcasting is performed using Facebook Prophet.

## Repository organisation

The project is organised as a series of Jupyter Notebooks. They are divided in a data preparation and a modelling part.

The data prep notebooks need to be executed in a given order.

Bitcoin data prep:
1. Prepare Bitcoin Dataframe.ipynb


Twitter data prep:
1. Scrape Tritter.ipynb
2. Sentiment Analysis Twitter.ipynb
3. LDA Twitter.ipynb
4. Daily Aggregation Twitter.ipynb


Reddit data prep:
1. Scrape Reddit.ipynb
2. Sentiment Analysis Reddit.ipynb
3. LDA Reddit.ipynb
4. Daily Aggregation Reddit.ipynb

Modelling notebooks are independent from each other and can be executed in any order after the data preparation.
