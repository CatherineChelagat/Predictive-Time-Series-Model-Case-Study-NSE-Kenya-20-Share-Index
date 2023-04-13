# Predictive Time Series Model Case Study NSE Kenya 20 Share Index
### Team Members:

1. Whitney Ngili
2. Catherine Chelagat
3. Gibson Wanjau
4. Bella Somwe
5. George Mungai

![nse](https://user-images.githubusercontent.com/117165965/231267951-21958356-66c9-4028-84b0-0ae2cf4a05dc.jpg)

## Introduction

The Nairobi Securities Exchange (NSE) is the principal securities exchange of Kenya, providing a platform for the buying and selling of various financial instruments, including stocks, bonds, and derivatives. The NSE is a key player in the East African capital markets, attracting local and international investors who seek to capitalize on the investment opportunities presented by the growing Kenyan economy.

The NSE 20 Share Index, launched in 1953, is one of the most widely followed stock market indices in East Africa, comprising the top 20 blue-chip companies listed on the NSE. The index serves as a benchmark for the overall performance of the Kenyan stock market and provides investors with an indication of the market sentiment and direction.

With the advent of technology and the availability of vast amounts of financial data, investors are increasingly turning to quantitative analysis and machine learning techniques to predict stock prices and generate alpha. In this project, we aim to develop a predictive time series model to forecast the stock prices of companies listed in the NSE, using a range of market-specific factors as inputs.

Our target partners for this project include SACCOs, insurance companies, and pension funds, who are important players in the Kenyan financial market. By developing a reliable time series model to forecast stock prices, we hope to provide our partners with valuable insights that can inform their investment decisions and enable them to optimize their portfolio returns.

The project will involve collecting and analyzing historical stock prices and market-specific factors, exploring the various time series models available, and developing and evaluating the performance of the selected model. The results of the project could provide valuable insights into the dynamics of the Kenyan stock market and inform investment decisions by local and international investors.

## Problem Statement

The Nairobi Securities Exchange (NSE) is the main securities exchange in Kenya, providing a platform for trading a range of financial instruments including equities, bonds, and derivatives. The NSE Share 20 Index is an index of the 20 largest and most actively traded stocks on the NSE, designed to provide a benchmark for the performance of the Kenyan stock market.

The ability to predict stock prices is of great interest to investors, traders, and financial analysts, as it can help them make informed decisions about buying and selling securities. Accurate stock price predictions can also be useful for companies seeking to raise capital through stock offerings, as they can better understand the potential value of their shares.

The Breakfast Club Consultancy is committed to leveraging machine learning techniques to predict the stock prices of the NSE Share 20 Index. By analyzing historical data on stock prices, as well as other economic and financial indicators, models will be trained that can forecast future prices with a high degree of accuracy. The goal is to provide investors, traders, and financial analysts with a valuable tool for making more informed decisions about buying and selling securities on the NSE.

## Main Objective

To develop and deploy a predictive time series model that leverages machine learning techniques to accurately forecast the stock prices of the Kenya NSE 20 Share Index, taking into account market-specific factors and historical data.

## Specific Objectives

- Develop and test machine learning models to identify the most significant market-specific factors that influence stock prices in the NSE.
- Evaluate the performance of the machine learning models in predicting future stock prices and compare them with traditional forecasting methods.
- Deploy the developed model online to provide easy access to our target partners, including SACCOs, insurance companies, and pension funds, who can use the model to inform their investment decisions.

## Notebook Structure
- Reading the Data
- Data Wrangling
- Exploratory Data Analysis
- Data Preprocessing
- Modelling
- Training final model on full dataset
- Conclusions
- Recommendations

## Data Understanding

The data used in this project was downloaded from [here](https://www.investing.com/indices/kenya-nse-20-historical-data) and [CBK website.](https://www.centralbank.go.ke/inflation-rates/)

The NSE 20 dataset contains 4531 rows and 6 columns with the following information:

No.	Column	Description
1	Date	Relevant date
2	Price	Average price of the stock
3	Open	Price at which the stock trades when an exchange opens for the day
4	High	Highest price the stock traded on that date
5	Low	Lowest price the stock traded on that date
6	Change %	Percentage change in stock price from the previous day

The data on exchange rate with the USD is downloaded from the investing website. It has 4729 rows and 6 columns with the columns having the same information as the NSE 20 dataset columns.

- The datasets from the CBK website are on the specific macroeconomic factors affecting the prices of shares. The following datasets have been downloaded:

- Inflation rates : This has 219 rows and contains the the percentage change in the monthly consumer price index (CPI).

- Annual GDP : This has 23 rows and contains the Kenyan GDP from 2000-2021

- Central Bank Rate : Data on this is found in two datasets, with one ranging from 2008-2023 and the other from 1991-2016. They contain the interest rate that the     Central Bank of Kenya charges on loans to banks.


## Methodology
### - Data Wrangling
Out of the several datasets that were collected, only some features and rows are relevant to the process. Therefore, in this step, the features that are not required from each dataset were dropped. The remaining datasets were then joined.
The cbk_rates datasets were in different formats, so before joining them, they needs to be adjusted. Since the data required should only be from 2005, any data before that were dropped.
### - Exploratory Data Analysis
 - Univariate analysis was perfomed. From the time series, the prices are highest in 2007 and then experiences a continous decline in 2008 all the way to 2009. This may have been as a result of the political instability caused by the post election violence. The prices are seen to keep following a similar trend over the years, increasing and decreasing in succession.
 - The CBK rates are seen to be almost constant from 2005 to 2007 before dipping and experiencing a continous drop up until 2011 before spiking again.The CBK rates are seen to be highest in 2012.This was as a result of high inflation rate and fiscal deficit. In 2016, CBK introduced a cap on their interest rates and this can be seen on the graph because there is a downward trend.
 - The exchange rate experienced a drop from 2005 to 2007 before going up since 2008 all the way to 2023. This can be attributed to increased rates of importing to exporting which has resulted to the weakening of the Kenyan Shilling against the dollar. The price being the lowest in 2008 is explained by the global recession that negatively affected the strength of the dollar. 
 - The inflation rates are seen to be fluctuating over the years, with the highest value being in 2012.
 - The GDP has been going up. This shows that the economy has been growing in an upward trajectory.
 - According to the heatmap, CBK rates are the most positively correlated to Price while the inflation rates are the most negatively correlated to Price.
 - According to the graphs above, the p-values are less than 0.05 which means that both Price and Inflation rates can be used to predict the other hence showing possible causality.


### - Data Preprocessing
 - From the graph, the data does not appear to be stationary since the rolling mean is not constant.
 - The p-value was 0.32 therefore we failed to reject the null hypothesis and determined that the data is not stationary. The data needed to be differenced so that it becomes stationary and fit for modelling.

### - Modelling 
 - The ARIMA model had an MAE of 8.87 which means that our predictions for the daily stock prices will be off by kshs 8.87. However, the predictive power of this model for in the context of stock prices is questionable because it is heavily reliant on previous values to a point where the predicted values look like they're shifted from the actual values at a certain lag.
 - The prophet model gave a mean absolute error of 465.3 for a one year forecast. This means that if this model makes a prediction for the share price one year from now, it would be off by kshs 465.3.
 - The prophet model with additional regressor features gave a mean absolute error of 373.9 for a one year forecast. This means that if this model makes a prediction for the share price one year from now, it would be off by 373.9 Ksh.

According to the Prophet model, the coefficients give the following information:
 - For an increase in exchange rate by 1 Ksh with the US dollar, the share price decreases by 541.2 Kshs
 - For an increase in GDP by 1 million, the share price decreases by 262.8 Kshs
 - For an increase in inflation rate by 1%, the share price decreases by 87.4 Kshs
 - For an increase in CBK rate by 1%, the share price decreases by 85.1 Kshs
Changepoints are basically abrupt changes in a time series model which could be used as indicators of external factors affecting the trend.

It is possible that the changepoints are clustered at the end of the month because that is when businesses often close their books and release financial reports. This could lead to changes in the market sentiment, which could affect NSE values.

The mae for VAR model is 356.75 meaning that our predictions will err by kshs 356 on the yearly predictions.

Our metric of success was set such that the best performing model would be the one with the least value of MAE. In this case, that would be the VAR model. However, this model failed to capture the complexity of the dataset and its predictions are more or less in a straight line as seen in the evaluation. The prophet model with regressors was more detailed and gave more insight on the predictiond.


## Minimum Viable Product(MVP)

We chose the prophet model with additional regressors because it was more detailed and gave more insight on the predictions, it even shows the changepoints in the stock prices. For this reason, the best recommended model for this project is the Prophet model with regressors.
### - Future improvements
 -  We should incorporate economic and financial indicators into their stock price prediction models, such as inflation and CBK rates, as this can help to improve the accuracy of the predictions. By taking into account factors such as inflation and CBK rates, companies can create more accurate models that can better forecast future stock prices.


## Conclusions

- Stock prices are mostly influenced by the inflation and CBK Rates.

- Market anomalies like the Monday effect also largely influence the price at whick stocks trade at during the week.

- The prophet model with regressors is a better forecaster as compared to the traditional forecasting models like ARIMA.

- With the Prophet Model, as the prediction period is increased, the accuracy of the predictions gets weaker. Therefore, it is feasible for a short period of time.

## Recommendations
- *The company/developers could use additional data sources and incorporate more economic and financial indicators into the model.* Additionally, developers could experiment with different machine learning algorithms, such as deep learning and reinforcement learning, to improve the accuracy of the predictions of the prophet model.

- *Continuously update and retrain the model*: Stock market data is constantly changing, so it's important to regularly update and retrain the model to ensure it remains accurate and effective. As new data becomes available, incorporate it into the model and retrain it to improve its accuracy.

- *Companies should consider incorporating economic and financial indicators into their stock price prediction models*, such as inflation and CBK rates, as this can help to improve the accuracy of the predictions. By taking into account factors such as inflation and CBK rates, companies can create more accurate models that can better forecast future stock prices.

- *Companies should use the prophet model with regressors for stock price predictions*, as it is more accurate than traditional forecasting models like ARIMA. The prophet model is designed to account for trends, seasonality, and other market anomalies, making it more effective at predicting future stock prices.

- *Companies should account for market anomalies when making stock price predictions*, such as the Monday effect, as these can have a significant influence on stock prices. By taking into account factors like the Monday effect, companies can ensure that their stock price predictions are as accurate as possible.

- *Investors, traders, and financial analysts should leverage machine learning techniques to generate more accurate stock price predictions.* By using advanced algorithms and large datasets, machine learning models can uncover patterns in the data that can be used to make more accurate predictions.

- *Use the model as a tool, not a crystal ball*: While the model is an effective tool for predicting stock prices, it's important to remember that it's not infallible. Encourage stakeholders to use the model as one of many tools in their investment decision-making process and to consider additional factors such as risk tolerance, diversification, and market trends.
