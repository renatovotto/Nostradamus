# Trading Tesla with Machine Learning and Sentiment Analysis

An interactive program to train a Random Forest Classifier to predict Tesla daily prices using technical indicators and sentiment scores of Twitter posts, backtesting the trading strategy and producing performance metrics.

The project leverages techniques, paradigms and data structures such as:

- Functional and Object-Oriented Programming
- Machine Learning
- Sentiment Analysis
- Concurrency and Parallel Processing
- Direct Acyclic Graph (D.A.G.)
- Data Pipeline
- Idempotence

## Scope

The intention behind this project was to implement the end-to-end workflow of the backtesting of an **Algorithmic Trading** strategy in a program with a sleek interface, and with a level of automation such that the user is able to tailor the details of the strategy and the output of the program by entering a minimal amount of data, partly even in an interactive way. This should make the program reusable, meaning that it's easy to carry out the backtesting of the trading strategy on a different asset. Furthermore, the **modularity** of the software design should facilitate changes to adapt the program to different requirements (i.e. different data or ML models).

## Strategy Backtesting Results

The Random Forest classifier model was trained and optimised with the **scikit-learn GridSearchCV** module. After computing the trading signals predictions and backtesting of the strategy, the following performances were recorded:

|                                  | Performance Indicators Summary |
|----------------------------------|--------------------------------|
| Return Buy and Hold (%)          | 1547.7                         |
| Return Buy and Hold Ann. (%)     | 297.6                          |
| Return Trading Strategy (%)      | 2411.95                        |
| Return Trading Strategy Ann. (%) | 389.4                          |
| Sharpe Ratio Ann.                | 17.74                          |
| Total Number of Trades           | 251                            |
| Hit Ratio (%)                    | 93.63                          |
| Average Trades Profit (%)        | 1.07                           |
| Average Trades Loss (%)          | -0.14                          |
| Max Drawdown (%)                 | -1.42                          |
| Days Max Drawdown Recovery       | 2                              |

![drawdown](https://user-images.githubusercontent.com/68741036/127544806-98215a1a-710d-408e-9073-e8d8a7c6bef7.png)

![returns](https://user-images.githubusercontent.com/68741036/127544828-a2a07608-7144-4f0d-b5f9-49ac807ef724.png)

## Running the Program

This is straightforward. There are very few variables and methods to initialise and call in order to run the whole program.  

Let me illustrate it in the steps below:

1. Provide the variables in `download_params`, a dictionary containing all the strategy and data downloading details.

    ```python
    download_params = {'ticker' : 'TSLA',
                       'since' : '2010-06-29', 
                       'until' : '2021-06-02',
                       'twitter_scrape_by_account' : {'elonmusk': {'search_keyword' : '',
                                                                   'by_hashtag' : False},
                                                      'tesla': {'search_keyword' : '',
                                                                'by_hashtag' : False},
                                                      'WSJ' : {'search_keyword' : 'Tesla',
                                                               'by_hashtag' : False},
                                                      'Reuters' : {'search_keyword' : 'Tesla',
                                                                   'by_hashtag' : False},
                                                      'business': {'search_keyword' : 'Tesla',
                                                                   'by_hashtag' : False},
                                                      'CNBC': {'search_keyword' : 'Tesla',
                                                               'by_hashtag' : False},
                                                      'FinancialTimes' : {'search_keyword' : 'Tesla',
                                                                          'by_hashtag' : True}},
                       'twitter_scrape_by_most_popular' : {'all_twitter_1': {'search_keyword' : 'Tesla',
                                                                           'max_tweets_per_day' : 30,
                                                                           'by_hashtag' : True}},
                       'language' : 'en'                                      
                       }
    ```

2. Initialise an instance of the `Pipeline` class:

    ```python
    TSLA_data_pipeline = Pipeline()
    ```

3. Call the `run` method on the `Pipeline` instance:

    ```python
    TSLA_pipeline_outputs = TSLA_data_pipeline.run()
    ```
    
    This will return a dictionary with the `Pipeline` functions outputs, which in this example has been assigned to     `TSLA_pipeline_outputs`. It will also print messages about the status and operations of the data downloading and manipulation process.

4. Retrieve the path to the aggregated data to feed into the `Backtest_Strategy` class:

    ```python
    data = glob.glob('data/prices_TI_sentiment_scores/*')[0]
    ```

5. Initialise an instance of the `Backtest_Strategy` class with the `data` variable assigned in the previous step.

    ```python
    TSLA_backtest_strategy = Backtest_Strategy(data)
    ```

6. Call the `preprocess_data` method on the `Backtest_Strategy` instance:
    
    ```python
    TSLA_backtest_strategy.preprocess_data()
    ```
    
    This method will show a summary of the data preprocessing results such as missing values, infinite values and features statistics.

From this point the program becomes interactive, and the user is able to input data, save and delete files related to the training and testing of the Random Forest model, and proceed to display the strategy backtesting summary and graphs.

7. Call the `train_model` method on the `Backtest_Strategy` instance:

    ```python
    TSLA_backtest_strategy.train_model()
    ```
    
    Here you will be able to train the model with the **scikit-learn GridSearchCV**, creating your own parameters grid, save and delete files containing the parameters grid and the best set of parameters found.

8. Call the `test_model` method on the `Backtest_Strategy` instance:

    ```python
    TSLA_backtest_strategy.test_model()
    ```
    
    This method will allow you to test the model by selecting one of the model's best parameters files saved during the training process (or the "default_best_param.json" file created by default by the program, if no other file was saved by the user).
    
    Once the process is complete, it will display the testing summary metrics and graphs.
    
    If you are satisfied with the testing results, from here you can display the backtesting summary, which equates to call the next and last method below. In this case, the program will also save a csv file with the data to compute the strategy performance metrics.

9. Call the `strategy_performance` method on the `Backtest_Strategy` instance:

    ```python
    TSLA_backtest_strategy.strategy_performance()
    ```
    
    This is the method to display the backtesting summary shown above in this document. Assuming a testing session has been completed and there is a csv file for computing the performance metrics, the program will display the backtesting results straight away using the existing csv file, which in turn is overwritten every time a testing process is completed. Otherwise, it will prompt you to run a training/testing session first.

### Tips
If the required data (historical prices and Twitter posts) have been already downloaded, the only long execution time you may encounter is during the model training: the larger the parameters grid search, the longer the time. I recommend that you start getting confident with the program by using the data already provided within the repo (backtesting on Tesla stock).

This is because any downloading of new data on a significantly large period of time such to be reliable for the model training will likely require many hours, essentially due to the Twitter scraping process.

That said, please be also aware that **as soon as you change the variables in the `download_params` dictionary and run the `Pipeline` instance, all the existing data files will be overwritten.** This is because the program recognise on its own the relevant data that need to be downloaded according to the parameters passed into `download_params`, and this is a deliberate choice behind the program design.

That's all! Clone the repository and play with it. Any feedback welcome. 

## Disclaimer

Please be aware that the content and results of this project do not represent financial advice. You should conduct your own research before trading or investing in the markets. Your capital is at risk.

## References

- [Minna Castoe, "Predicting Stock Market Price Direction with Uncertainty Using Quantile Regression Forest", Uppsala University (2020)](https://www.diva-portal.org/smash/get/diva2:1503760/FULLTEXT02)
- [Venkata Sasank Pagolu, Kamal Nayan Reddy, Ganapati Panda, Babita Majhi. Sentiment analysis of Twitter data for predicting stock market movements, 2016 International Conference on Signal Processing, Communication, Power and Embedded System (SCOPES)](https://ieeexplore.ieee.org/abstract/document/7955659/metrics#metrics)
- [Random Forest](https://en.wikipedia.org/wiki/Random_forest)
- [Directed Acyclic Graph (DAG)](https://www.capgemini.com/gb-en/2020/10/introducing-directed-acyclic-graphs-and-their-use-cases/)
- [Dataquest Data Engineer course](https://www.dataquest.io/path/data-engineer/)
- [Idempotence](https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation)