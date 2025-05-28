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

### Project Summary: Predictive Analysis of Portfolio Returns (DSA210)

#### Project Goal

The objective of this project is to analyze and predict the daily return direction (positive or negative) of a portfolio constructed from three financial assets: KYD Eurobond Index, BIST 100 Index, and Gold (Ounce/USD). The study also compares the performance of this portfolio with the KYD 1-Month Deposit Index.

#### Data and Preparation

* **Data Source**: Daily price data of various financial instruments from 2010 to 2024, provided by Hedef Portfoy.
* **Assets Used**: KYD Eurobond, BIST 100, Gold USD/Ounce, and KYD Deposit Index.


1. **Data Loading**

   * Loaded the `.xlsx` file using Google Colab.

2. **Return Calculations**

   * Calculated daily returns for KYD Eurobond, BIST 100, and Gold.
   * Created an equal-weighted portfolio from the average of the three assets.
   * Calculated daily returns for the KYD 1-Month Deposit Index.

3. **Target Variable Creation**

   * Defined a binary target variable `Target`, where:

     * `1` indicates the portfolio return is positive,
     * `0` indicates otherwise.

4. **Data Visualization and Cleaning**

   * Plotted time series to visualize asset performance.
   * Used z-score filtering to remove extreme outliers from portfolio returns.

5. **Hypothesis Testing**

   * Null Hypothesis (H0): There is no significant difference between the portfolio return and deposit return.
   * Alternative Hypothesis (H1): The portfolio return is significantly different from the deposit return.
   * Result: p-value < 0.05 → Reject H0 → The portfolio performs significantly different than the deposit.

6. **Machine Learning Model**

   * Logistic Regression was applied to classify the direction of daily return.
   * Features: `Portfolio`, `Deposit`, `Lag_1`, `Lag_2`
   * Train-test split (70-30), with feature scaling.
   * Balanced class weights used to address class imbalance.
   * Model accuracy exceeded 98%, indicating strong predictive performance.


### Hypothesis and Methodology 

This study aims to investigate whether the daily return of a portfolio consisting of KYD Eurobond, BIST 100, and Gold (USD/Ounce) can be predicted using past return patterns and other financial indicators.
The research is driven by the following hypotheses:

* **H₀ (Null Hypothesis):**
  The daily return of the portfolio cannot be accurately predicted using lagged returns and other financial indicators.

* **H₁ (Alternative Hypothesis):**
  The daily return of the portfolio can be accurately predicted using lagged returns and other financial indicators.

To test this hypothesis, a logistic regression model was trained using features such as portfolio return, 1-month KYD deposit return, and lagged values of the portfolio (`Lag_1`, `Lag_2`). The model was evaluated using accuracy, precision, recall, and F1-score metrics, as well as ROC and precision-recall curves. The results showed that the model achieved over 98% accuracy, confirming the hypothesis that portfolio direction (positive or negative) can be reliably predicted based on historical data.

#### Conclusion

The hypothesis that portfolio returns can be predicted using historical patterns and financial indicators was supported by statistical testing and model performance. The logistic regression model proved effective in predicting the direction of returns. This analysis supports the viability of using basic financial features and lagged returns for short-term forecasting in a diversified portfolio.


