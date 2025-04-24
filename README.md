# DSA210
## Predictive Analysis of Asset Prices Using Machine Learning

### Project Motivation
This project is driven by the goal to understand and predict the asset prices using historical data from 2010 to 2024. By applying statistical analysis and machine learning, I aim to forecast future prices based on past trends, which could be highly beneficial for investment strategies and financial planning.

### Data Source
The dataset consists of price data for ten different assets from 2010 to 2024. This includes a variety of financial instruments such as bonds, stock indices, and commodities. It includes various KYD indexes such as Eurobond, short and long-term government bonds, and deposits. Additional key instruments in the dataset are the BIST 100 Index, S&P 500 Total Return Index, Gold/USD rate, and the US 10-Year Treasury Index. This diverse selection of local and international financial data provides a robust foundation for conducting extensive financial analysis and modeling. The table below showcases a snippet of the dataset used in the analysis.

| Date     | KYD Mevduat Index | KYD Eurobond Index | KYD Short Term Public| KYD Short Term Bond| KYD Mevduat  (1 Month) | KYD Long Term | BIST 100 Index | S&P 500 Total Return Index | Gold Ons/USD | ABD 10 Year Bond Index | Dolar/TL |
|----------|-------------------|--------------------|----------------|----------------|-------------|---------------|----------------|-----------------------------|--------------|------------------------|----------|
| 31.05.2010 | 100             | 219.27             | 219.27         | 100            | 156.65      | 100           | 729.36         | 2835.33367                 | 1905.33395   | 686.908635             | 1.5665   |
| 01.06.2010 | 100.024         | 220.43             | 220.43         | 100.05         | 158.001059  | 100.49        | 730.38         | 2810.626301                | 1936.609822  | 695.0264482            | 1.5799   |
| 02.06.2010 | 100.048         | 219.72             | 219.72         | 100.1          | 157.342025  | 101.23        | 740.46         | 2871.4833                  | 1924.88886   | 688.4511984            | 1.5732   |
| 03.06.2010 | 100.072         | 219.32             | 219.32         | 100.18         | 156.622884  | 101.87        | 743.07         | 2869.856248                | 1889.336645  | 683.7862507            | 1.5659   |
| 04.06.2010 | 100.096         | 219.89             | 219.89         | 100.19         | 157.764162  | 102.03        | 732.42         | 2791.202384                | 1924.231316  | 697.958316             | 1.5772   |


### Data Collection Methods
The historical price data was collected from reputable financial market databases, ensuring accuracy and reliability. Even though the market price data for these ten assets is available on the internet, I obtained it from a well-known portfolio company, Hedef Portföy.. The data for the first phase of the project has been processed to calculate statistical measures like expected returns and covariance matrices.

### Data Analysis Plan
The initial stage of data analysis involved calculating the expected returns and covariance matrices for the assets:
- **Expected Returns Calculation**: Returns will be calculated using daily prices with the formula `(Current Value - Original Value) / Original Value`. These daily returns will be then annualized using the formula `((Daily Return + 1)^252) - 1`, reflecting the 252 trading days in a year.
- **Covariance Matrix Calculation**: With the annualized returns for each asset, the covariance between each pair of assets will be calculated using the standard formula for covariance:
**Covariance(X, Y) = E[(X - μX)(Y - μY)]**
where X and Y are the annualized returns of two assets, and μX and μY are their respective mean returns. The expectation E is estimated as the average over the observed period. This calculation provides a matrix where each element σij represents the covariance between the returns of asset i and asset j. Positive values indicate that assets tend to move in the same direction, whereas negative values suggest inverse movements.

#### Significance:
The covariance matrix is fundamental in modern portfolio theory, used to construct a portfolio that optimally balances return and risk. By understanding the covariance between assets, investors can diversify their holdings to minimize risk while aiming for desired returns. This is particularly valuable in strategic decision-making for long-term investments.

### Possible Limitations
The current analysis may be limited by the variability in financial markets and the complexity of global economic factors.

### Machine Learning Proposal Goals
The next phase will involve using machine learning techniques to predict asset prices for the first three months following the dataset. Models like ARIMA, or regression analysis might be utilized to forecast based on patterns identified in the historical data.

### Data Collection, EDA, and Hypothesis Testing:  
[Open EDA & Hypothesis Test Notebook](Data_Collection,_EDA,_and_Hypothesis_Testing.ipynb)

[Exploratory Financial Analysis and Hypothesis Testing](Exploratory_Financial_Analysis_and_Hypothesis_Testing.ipynb)

As part of the April 18 milestone, I successfully collected and analyzed a dataset consisting of 11 financial assets with daily price data from 2010 to 2024. I performed extensive exploratory data analysis, including checking data types, identifying and handling missing values, and generating descriptive statistics. Time series plots highlighted long-term trends in asset performance, and correlation analysis revealed strong relationships among most KYD-based indices, while long-term bonds demonstrated weaker or even negative correlations—indicating diversification potential. A one-sample t-test was conducted on the daily returns of the KYD Deposit Index, confirming that its mean return is statistically different from zero (p < 0.0001). These steps provide a solid foundation for the next phase of the project, where machine learning models will be applied for price forecasting.

### Refined Hypothesis: Portfolio vs. Benchmark
Hypothesis Statement:The average daily return of the portfolio—composed of the KYD Eurobond Index, BIST 100 Index, and Gold Ounce/USD Rate with equal weighting—is statistically significantly higher than the average daily return of the KYD Deposit Index (1 Month).

In this analysis, I constructed an equally weighted portfolio consisting of the KYD Eurobond Index, BIST 100 Index, and the Gold Ounce/USD Rate. The objective was to evaluate whether this portfolio statistically outperformed a risk-free benchmark, the KYD Deposit Index (1 Month), in terms of average daily return. A paired sample t-test was applied for this purpose. While the cumulative return plot visually shows that the portfolio slightly outperformed the benchmark over time, the statistical results (t = 0.8071, p = 0.4197) indicate that this difference is not statistically significant at the 5% level. 

Thus, although the portfolio outperformed the benchmark during certain periods, this advantage was not consistent or strong enough to reject the null hypothesis. These findings emphasize the importance of complementing return-based evaluations with statistical validation when assessing the effectiveness of investment strategies.







