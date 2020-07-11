# **FINTECH BOOTCAMP PROJECT 2**
# **Stock Trading With Sentiment Analysis**
## **Prepared By:**
* **Samir Sidi** 
* **Kevin Lacap** 
* **Matt Newman** 
* **Subash Mishra** 

# **Introduction**
![](https://cdn.benzinga.com/files/imagecache/1024x768xUP/images/story/2012/shutterstock_101193922_0.jpg)

## **Algorithmic Trading:** 
### Algo trading automates the trading process in financial markets by rapidly and precisely executing orders based on a set of defined rules. It removes human error and the dangers of acting on emotion. 

## **Sentiment Analysis:**
![](https://d1rwhvwstyk9gu.cloudfront.net/2017/07/Crowsourced-Sentiment-Analysis-Strategy_2.jpg)
### Stock trading is highly influenced by the sentiment of news headlines, comments on social media, and internet platforms. It's impossible to read all tweets or news in very short period time because the effect of this in stock price is fast. So, the Natural Language Processing tools and Algorithmic Trading would make this a lot easier. A well-set program could potentially scan all sorts of text over the millions of webpages and social media to determine the subjective information or emotional state of the writer. In this project we are using VADER library to rank the sentiments of news related to our chosen stock to determine Entry/Exit signals. 

## **Overview:** 

### In this project we are going to use python, pandas, plotly, Natural Language and Deep Learning libraries to build a platform which helps us to guide when to buy and sell the particular stock. 

### The main research question we try to address is how we can determine the Entry/Exit position while trading. This is important for several reasons: 

* A better Algo-trading model likely to assure greater chance for investor to reach their financial goals;

* Stock prices are affected by the news and comments in social media. So, as this model scan linguistic sentiments, it builds up investor's confidence during stock trading;

* It able to rank how positiveness or negativeness of news headlines.


## **Fetching Data from API:**
### In order to ensure reliability and validity of this model, it is important to have an authentic data source to run our analysis. In this project we are using Yahoo API which able us to pull raw stock data from internet to our working platform in real-time. Yahoo API allows us to grab adjusted close than just regular close which makes our analysis more accurate and reliable. For this project we going to be using stock of Boeing as default tickers but we will have an interactive platform to pass any tradable ticker(s). For the demonstration we have selected last week trading data.

## Data Table
![](https://github.com/MishraSubash/project-Repo-/blob/master/table1.png)




## *Challenges while cleaning data*
### Rather than jumping directly in process of data cleaning, we realized which 'Close' should be used. We think it important to address this question. The regular 'Close' doesn't reflect recent divided announcement and stock splits so we thought this is important to include in our model. Adjusted Close is for accuracy and reliability. 

## **Data Analysis, Crossover Fitting and Average Moving Calculation**
### This is a backbone of our project where we present the framework of analysis and discuss challenges and outcomes. 

## **The Moving Averages:**
### [A Moving Average (MA)](https://www.investopedia.com/terms/m/movingaverage.asp) is a widely used technical indicator that smooths out price trends by filtering out the “noise” from random short-term price fluctuations. Moving averages can be constructed in several different ways, and employ different numbers of days for the averaging interval. In our project we use 9 trading days for Short Moving Average (SMA_9) and 50 days for Long Moving average (SMA_50). An MA with a short time frame will react much quicker to price changes than an MA with a long look back period. In the figure below, the 9-day moving average more closely tracks the actual price than the 50-day moving average does. 

## **Trading Strategies—Crossovers** 
### Crossovers are one of the main moving average strategies. The first type is a price crossover, which is when the price crosses above or below a moving average to signal a potential change in trend. When the shorter-term MA crosses above the longer-term MA, it's a buy signal, as it indicates that the trend is shifting up. This is known as a "golden cross." 

### Meanwhile, when the shorter-term MA crosses below the longer-term MA, it's a sell signal, as it indicates that the trend is shifting down. This is known as a "dead/death cross".


## *Challenges while implementing Moving Averages*
### Moving averages are calculated based on historical data, and nothing about the calculation is predictive in nature. One major problem is that, if the price action becomes choppy, the price may swing back and forth, generating multiple trend reversal or trade signals. Moving averages work quite well in strong trending conditions but poorly in choppy or ranging conditions. Adjusting the time frame can remedy this problem temporarily, although at some point, these issues are likely to occur regardless of the time frame chosen for the moving average(s). 

### We found the following result while using short and long moving averages. 
![](https://github.com/MishraSubash/project-Repo-/blob/master/SMA%20vs%20LMA1.png)


# **Sentiment Analysis:**
![](https://github.com/MishraSubash/project-Repo-/blob/master/Face_image1.png)
## **News Trading Strategy**
### We are using newsapi API to fetch major news headlines in our working platform. We run code to look over 100 webpages to look into the news articles related to our ticker(s) then we deploy NLTK library for building programs for text analysis. NLTK platform provides us with a powerful tool for working with natural language processing (NLP). Along with this we combine VADER library to analyses sentiment of the text we fetched from newsapi. 

## **VADER Analysis and Trade Signals:** 
### We are using VADER (Valence Aware Dictionary for sEntiment Reasoning) library for the sentiment analyses section which uses fewer resources and no need for vast amounts of training data. VADER is sensitive to both polarity (both positive and negative) and intensity (how positive or negative is sentiment) of emotions. It measures the sentiment on a scale from -4 to +4, where -4 stands for the most "Negative" and +4 for the most "positive" sentiment. We rank sentiment for each days using numeric scores. If the combine is greater the 0.20, it is considered as Buy signal and less -0.20 consider as exit. We obtain following table while scoring sentiments


### VADER ENTRY/EXIT analyses in graph
![](https://github.com/MishraSubash/project-Repo-/blob/master/entry%20exit%201.png)


### COMBINE Result: Following graph is the combine result of core trading and trading with sentiment analysis. 

![](https://github.com/MishraSubash/project-Repo-/blob/master/sma%20lma%20sentiment1.png)

## **Findings:** 
### Sentiment analysis allows you to automatically identify the emotional tone in a text. Thanks to Natural Language Processing (NLP), it is possible to create systems that are able to understand the opinions present in all kinds of conversations and obtain valuable insights about products or services. In our project we found very interesting combination between stock price fluctuation and sentiment of that stocks in news channels. Positive sentiments affect stock price goes up and negative sentiment goes down. The above combine graph can interpreted this result more effectively. 


## **Postmortem:** 
* As the number of tickers grows, it takes longer time to fetch data in a working platform and very difficult to achieve an optimum employing that set-up. 
* If we have enough time, we would definitely to employ an initial investment amount for trading and see how profitable/losses we can see while algo-trading with sentiment. 

* In the future we would like to extend the analysis in different aspects: 
    * Build a more advanced interface for the user. 
    * Overlay plotly graphs
    * Longer period of back testing
    * Looking over social media platform 
    
## ```Work Cited For Conceptual Framework```
- [A Beginer's Guide for Sentiment Analysis](https://algotrading101.com/learn/sentiment-analysis-python/)
- [Sentiment Analysis using VADER](https://blog.quantinsti.com/vader-sentiment/)
- [Price Prediction Using Python](https://medium.com/@randerson112358/stock-price-prediction-using-python-machine-learning-e82a039ac2bb)
