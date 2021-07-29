# Nostradamus

## Trading Tesla with Machine Learning and Sentiment Analysis

An interactiive program to train a Random Forest classifier to predict Tesla daily prices using technical indicators and Twitter sentiment scores, backtesting the strategy and producing performance metrics.

The project leverages techniques, paradigms and data structures such as:

- Functional and Object Oriented Programming
- Machine Learning
- Sentiment Analysis
- Concurrency and Parallel Processing
- Direct Acyclic Graph (D.A.G.)
- Data pipelines
- Idempotence

<br>
<br>
### Scope

The intention behind this project was to implement the end-to-end workflow of the backtesting of an **Algorithmic Trading** strategy in a program with a sleek interface, and with a level of automation such that the user is able to tailor the details of the strategy and the output of the program by entering a minimal amount of data, partly even in an interactive way. This should make the program reusable, meaning that it's easy to carry out the backtesting of the trading strategy on a different asset. Furthermore, the **modularity** of the software design should facilitate changes to adapt the program to different requirements (i.e. different data or ML models).

<br>
<br>
### Strategy Backtesting Results

The Random Forest classifier model was trained and optimised with the **scikit-learn GridSearchCV** module. After computing the trading signals, the following performances were recorded:

![drawdown](https://user-images.githubusercontent.com/68741036/127544806-98215a1a-710d-408e-9073-e8d8a7c6bef7.png)

![returns](https://user-images.githubusercontent.com/68741036/127544828-a2a07608-7144-4f0d-b5f9-49ac807ef724.png)

<br>
<br>
### Disclaimer

Please be aware that the content and results of this project do not represent financial advise. You should conduct your own research before trading or investing in the markets. Your capital is at risk.

<br>
<br>
### References

- [Minna Castoe, "Predicting Stock Market Price Direction with Uncertainty Using Quantile Regression Forest", Uppsala University (2020)](https://www.diva-portal.org/smash/get/diva2:1503760/FULLTEXT02)
- [Venkata Sasank Pagolu, Kamal Nayan Reddy, Ganapati Panda, Babita Majhi. Sentiment analysis of Twitter data for predicting stock market movements, 2016 International Conference on Signal Processing, Communication, Power and Embedded System (SCOPES)](https://ieeexplore.ieee.org/abstract/document/7955659/metrics#metrics)
- [Random Forest](https://en.wikipedia.org/wiki/Random_forest)
- [Directed Acyclic Graph (DAG)](https://www.capgemini.com/gb-en/2020/10/introducing-directed-acyclic-graphs-and-their-use-cases/)
- [Dataquest Data Engineer course](https://www.dataquest.io/path/data-engineer/)
- [Idempotence](https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation)
