# Portfolio Optimization using Deep Reinforcement Learning

# Summary

Financial portfolio optimization is the process of redistributing funds into multiple financial vehicles at a given timestamp in order to maximize returns while minimizing the risk at the same time. The goal in this project is to provide a solution framework which deals with this complex financial engineering problem. The framework will be implemented using a combination of machine learning and Reinforcement Learning (RL) techniques. Built RL framework will be trained and tested on stocks and crypto currency trading data.

The dataset consists of:

(i)  Historical trading data for 15 stocks from S&P 500 portfolio<sup>1</sup> from 2005 to present.

(ii) Historical trading data for 6 Cryptocurrencies from CoinMarketCap<sup>2</sup> and Poloniex Exchange<sup>3</sup> from 2015 to present.

The price data follows the format of Open, High, Low and Close (OHLC) for a given time frame. Open is the price at which the stock begins trading, High is the highest value it attains, Low is the lowest value throughout the day and Close is the closing value. For stocks data, the time frame considered is one trading day whereas for cryptocurrency data, time frame considered is 24 hours for phase 1 and 30 minutes for phase 2. Usually, open price is equal to close price for the previous day, but cryptocurrency follows high frequency trading, thus we might not see open price for a time step same as closing price for previous time steps. 

To build a better portfolio optimizing agent than the one obtained in phase 1, where the baseline solution framework was built using Convolutional Neural Network (CNN), another framework will be built using Long Short-Term Memory (LSTM). Another evaluation metric, Maximum Drawdown will be introduced apart from Sharpe Ratio and Benchmarks.


# Proposed plan of research

In the first phase of the project, the trading period for cryptocurrency data was discretized by considering a time window of 24 hours which does not efficiently capture the fact that the exchanges are open 24/7 without restricting frequency of trading and should not ideally be directly applied to portfolio selection problems. But capturing the continuous nature is found to be difficult and even unstable sometimes. Therefore, non-stop markets are ideal for machines to learn in the real world in shorter timeframes and thus the results generated by considering a trading period of every 30 minutes will be explored and tested in the second phase.

Furthermore, the preliminary results show that the baseline solution framework produced a sub optimal agent for stocks data and a near optimal agent for the cryptocurrency data. For the second phase of the project, one of the goals would be to achieve a more optimal agent for both stocks and cryptocurrency data than the one produced by baseline solution framework by experimenting with a different network architecture like Long Short-Term Memory( LSTM) to build the policy function. LSTM neural networks are generally better at learning historical data and time series forecasting than other standard feed forward neural networks.

Although back testing using Sharpe Ratio is a better evaluation metric than benchmark testing as it considers volatility of the portfolio values, but it equally treats upwards and downwards movements. In reality upwards volatility contributes to positive returns, but downwards to loss. In order to highlight the downwards deviation, Maximum Drawdown (MDD) evaluation metric will also be used. Maximum Drawdown (MDD) is the maximum observed loss from a peak to a trough of a portfolio, before a new peak is attained. Maximum drawdown is an indicator of downside risk over a specified time period.

# Preliminary results

In order to build a portfolio optimizer, 15 assets for stock data based on lesser correlation and 6 assets for cryptocurrencies based on trading volume were considered. A deep Reinforcement learning method was applied and a Convolution Neural Network model was built. The results from the model have been analysed and will be considered as a baseline for the second phase of the project.

On testing the performance of optimizing agent over stocks data, the final weights allocated to different assets can be seen in figure 1. The highest weight was assigned to Coca-Cola Co. followed by Verizon Communications Inc and Walmart Inc. The least weight was assigned Simon Property Group Inc followed by Xcel Energy Inc.

![wt_vectors_stocks[]{label="fig:wt_vectors_stocks"}](figures/wt_vector_stocks_cnn.png)
###### Figure 1: Weights obtained for stocks portfolio

As seen in Figure 2 that represents the cumulative portfolio value across test steps, the value returned by the built optimising agent increased with each test step and performed better when compared to the values returned by the agent assigning equal weights amongst all the assets. 
The optimizing agent exhibited an increase of 25-30% in cumulative portfolio value over the initial portfolio value.


![cpv_stocks[]{label="fig:cpv_stocks"}](figures/cpv_stocks_cnn.png)
###### Figure 2: Cumulative Portfolio Value for Stocks portfolio

The mean sharpe ratio obtained for the optimizing agent in case of stocks data is 0.735. As mentioned earlier since the sharpe ratio is less than 1, the results obtained in figure 2 is misleading and the trained agent gives us sub-optimal results for stocks data.

On testing the performance of optimizing agent over crypto data, the final weights allocated to different assets can be seen in figure 3. The highest weight was assigned to Litecoin followed by XRP(Ripple) and Ethereum. The least weight was assigned to Monero followed by NEM(XEM).

![wt_vectors_crypto[]{label="fig:wt_vectors_crypto"}](figures/wt_vector_crypto_cnn.png)
###### Figure 3: Weights obtained for Crypto portfolio

As seen in Figure 4 that represents the cumulative portfolio value across test steps, the value returned by the built optimising agent increased with each test step and performed better when compared to the values returned by the agent assigning equal weights amongst all the assets. 
The optimizing agent exhibited an increase of 300-400% in cumulative portfolio value over the initial portfolio value. The equiweight agent also performed well here exhibiting an increase of around 200% in cumulative portfolio value over the initial portfolio value


![cpv_crypto[]{label="fig:cpv_crypto"}](figures/cpv_crypto_cnn.png)
###### Figure 4: Cumulative Portfolio Value for Crypto portfolio

The mean sharpe ratio obtained for the optimizing agent in case of crypto currency data is 1.652. As mentioned earlier, since the sharpe ratio is greater than 1, the results obtained in figure 4 is acceptable and the trained agent gives us nearly optimal results for crypto currency data.


# References

[1] Historical stocks data of 15 assets from SP 500 portfolio from 2005 to present. https://www.barchart.com

[2] Historical data for 6 Cryptocurrencies from CoinMarketCap from 2015 to present. https://coinmarketcap.com

[3] 10 Cryptocurrency Data from Poloniex Exchange. https://poloniex.com/

[4] Chi Zhang, Corey Chen, Limian Zhang https://www-scf.usc.edu/~zhan527/post/cs599/

[5] Olivier Jin, Hamza El-Saawy Portfolio Management using Reinforcement Learning Dept. of Computer Science, Stanford, USA.

[6] Zhengyao Jiang, Dixing Xu, and Jinjun Liang A Deep Reinforcement Learning Framework for the Financial Portfolio Management Problem.
Xi’an Jiaotong-Liverpool University, Suzhou, SU 215123, P. R. China.
