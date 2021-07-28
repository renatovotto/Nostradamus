# Nostradamus

## H2

### H3

- list
- item

* another
* list

### another h3

In this project we will aim to use a Machine Learning model to predict the daily prices of the Tesla stock. Along with several technical indicators derived from the OHLCV data, we will feed into the model also the sentiment scores of relevant Twitter posts, thus leveraging Sentiment Analysis, a Natural Language Processing tecnique. All these data will be used to train the model which in turn will predict the trading signals.

Sentiment analysis and generally the positive or negative sentiment on news about a stock has been studied in depth in the recent years, finding a strong correlation between the sentiment score of such data and the stock price movement.

The labels we need to predict are the buy and sell signals, which we will assign based on simple price conditions in order to train the model. Since these are discrete data, the problem we are trying to solve is a supervised classification.

The Machine Learning model we wil use is the Random Forest Classifier. Random Forests are supervised algorithms consisting in multiple decision trees performing well with non-linear data and with low risk of overfitting. They are also strong against outliers, although they suffer of low interpretability compared to single decison trees.

The reliability of the Random Forest in predicting stock prices is widely confirmed by many studies, suggesting the robustness of this model when compared to other machine learning algorithms. The paper "Predicting Stock Market Price Direction with Uncertainty Using Quantile Regression Forest" raises an observation regarding the uncertainty of predictions of the Random Forest model, stating that it's scarcely studied subject. This is surely an aspect worth to investigate for researchers, given the financial risk involved with applications such as algorhitmic trading.

In this project we will also leverage techniques and paradigms such as concurrency, functional and object oriented programming, idempotence, Direct Acyclic Graph and data pipeline.

The intention is to design a program with a sleek interface and with a level of automation such that the user is able to tailor the details and output of the program by entering a minimal amount of data, partly even in an interactive way. This should make the project reusable, meaning that it's easy to carry out the backtest of the trading strategy on another asset. Furthermore, the modularity of the software design should facilitate changes to adatpt the program to different requirements (i.e. different data or ML models).

Please be aware that the content and results of this project do not represent financial advise. You should conduct your own research before trading or investing in the markets. Your capital is at risk.
