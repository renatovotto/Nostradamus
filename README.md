# Nostradamus

## Trading Tesla with Machine Learning and Sentiment Analysis

An interactiive program to train a Random Forest classifier to predict Tesla daily prices using technical indicators and Twitter sentiment scores, backtest the strategy and produce strategy performance metrics.

The project leverages techniques, paradigms and data structures such as:

- Functional and Object Oriented Programming
- Machine Learning
- Sentiment Analysis
- Concurrency (Multi Processing and Multi Threading)
- Direct Acyclic Graph (D.A.G.)
- Data pipelines
- Idempotence


### Scope

The intention was to design an **Algorithmic Trading** backtest program with a sleek interface and with a level of automation such that the user is able to tailor the details and output of the program by entering a minimal amount of data, partly even in an interactive way. This should make the project reusable, meaning that it's easy to carry out the backtest of the trading strategy on another asset. Furthermore, the modularity of the software design should facilitate changes to adatpt the program to different requirements (i.e. different data or ML models).

### Strategy Backtest Results

After training the Random Forest classifier with the **scikit-learn GridSearchCV** and computing the trading signals, the following performances were recorded: 

### Disclaimer

Please be aware that the content and results of this project do not represent financial advise. You should conduct your own research before trading or investing in the markets. Your capital is at risk.


### References

- [Minna Castoe, "Predicting Stock Market Price Direction with Uncertainty Using Quantile Regression Forest", Uppsala University (2020)](https://www.diva-portal.org/smash/get/diva2:1503760/FULLTEXT02)
- [Venkata Sasank Pagolu, Kamal Nayan Reddy, Ganapati Panda, Babita Majhi. Sentiment analysis of Twitter data for predicting stock market movements, 2016 International Conference on Signal Processing, Communication, Power and Embedded System (SCOPES)](https://ieeexplore.ieee.org/abstract/document/7955659/metrics#metrics)
- [Random Forest](https://en.wikipedia.org/wiki/Random_forest)
- [Directed Acyclic Graph (DAG)](https://www.capgemini.com/gb-en/2020/10/introducing-directed-acyclic-graphs-and-their-use-cases/)
- [Dataquest Data Engineer course](https://www.dataquest.io/path/data-engineer/)
- [Idempotence](https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation)
