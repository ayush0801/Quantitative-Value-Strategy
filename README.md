# Quantitative Value Strategy

This project demonstrates a quantitative value investing strategy that selects the 50 stocks with the best value metrics from the S&P 500. The strategy involves calculating the recommended trades for an equal-weight portfolio of these 50 stocks, as well as a more advanced robust value strategy.

## Table of Contents
- [Introduction](#introduction)
- [Library Imports](#library-imports)
- [Importing Stock Data](#importing-stock-data)
- [Making API Calls](#making-api-calls)
- [Filtering Value Stocks](#filtering-value-stocks)
- [Calculating Shares to Buy](#calculating-shares-to-buy)
- [Advanced Value Strategy](#advanced-value-strategy)
- [Saving to Excel](#saving-to-excel)
- [Calculating Returns](#calculating-returns)
- [Investment Strategy using 80-20 Principle](#investment-strategy-using-80-20-principle)
- [Visualizing Returns](#visualizing-returns)
- [Acknowledgements](#acknowledgements)

## Introduction

"Value investing" means investing in the stocks that are cheapest relative to common measures of business value (like earnings or assets). This project builds an investing strategy that selects the 50 best value stocks and calculates recommended trades for an equal-weight portfolio of these stocks.

## Library Imports

The project utilizes the following libraries:
- `numpy`
- `pandas`
- `requests`
- `math`
- `scipy.stats`
- `xlsxwriter`

 Make sure to install the required libraries.
   ```sh
   pip install numpy pandas requests xlsxwriter scipy
   ```



## Importing Stock Data

We import a list of S&P 500 stocks from a CSV file.

## Making API Calls

The project uses the IEX Cloud API to fetch value metrics for each stock, including:
- Price-to-earnings ratio (P/E ratio)
- Price-to-book ratio (P/B ratio)
- Price-to-sales ratio (P/S ratio)
- Enterprise value divided by EBITDA (EV/EBITDA)
- Enterprise value divided by gross profit (EV/GP)

## Filtering Value Stocks

The top 50 stocks by combined value metrics are selected and sorted.

## Calculating Shares to Buy

A function calculates the number of shares to buy for each selected stock based on the given portfolio size.

## Advanced Value Strategy

The strategy is refined by considering multiple value metrics, selecting stocks from the lowest percentiles of:
- Price-to-earnings ratio
- Price-to-book ratio
- Price-to-sales ratio
- Enterprise value divided by EBITDA (EV/EBITDA)
- Enterprise value divided by gross profit (EV/GP)

Each stock is assigned a percentile rank for each metric, and the average of these percentiles (RV score) determines the top value stocks.

## Saving to Excel

The results are saved to an Excel file using `xlsxwriter`, with formatted columns for better readability.

## Calculating Returns

The returns for the selected value stocks are calculated over different timeframes, using the following steps:
1. **Fetch Historical Price Data**: Retrieve the historical prices for each stock.
2. **Calculate Returns**: Compute the returns for each selected stock over the specified timeframes (e.g., 1 month, 3 months, 6 months, and 1 year).
3. **Aggregate Returns**: Aggregate the returns for the entire portfolio.

## Investment Strategy using 80-20 Principle

An alternative investment strategy based on the 80-20 principle is implemented. In this strategy, 80% of the portfolio size is allocated to the top 20% of stocks based on the RV (Robust Value) Score, and the remaining 20% of the portfolio size is allocated to the rest of the stocks.

The code iterates through the stocks in `rv_dataframe` and calculates returns for each timeframe (one month, three months, six months, and one year) using the 80-20 allocation principle. For the top 20% of stocks, 80% of the portfolio size is allocated, and for the remaining 80% of stocks, 20% of the portfolio size is allocated.

Ensure to adjust the `portfolio_size` variable as per your portfolio setup before running the code.

## Visualizing Returns

The project includes a section to visualize and compare the returns of two different investment strategies:
- **Equal Weighting**: Allocating an equal amount of capital to all selected stocks.
- **Unequal Weighting (80-20 Principle)**: Allocating 80% of the portfolio to the top 20% of stocks based on the RV Score, and 20% to the remaining 80% of stocks.

To visualize the returns, the project uses `matplotlib` to generate a bar graph showing the returns for different timeframes (1 month, 3 months, 6 months, and 1 year).

The steps to generate the visualization include:
1. **Calculate Returns**: Compute the returns for each selected stock over the specified timeframes.
2. **Aggregate Returns**: Aggregate the returns for the entire portfolio under both strategies.
3. **Plot the Graph**: Use `matplotlib` to create a bar graph comparing the returns of the two strategies.

By visualizing the returns, you can easily compare the performance of the equal-weight and 80-20 principle strategies across different timeframes.

The following graph shows the comparison of returns over different timeframes using the 80-20 investment strategy:

![Returns Comparison](https://i.postimg.cc/6pBFBWfY/Untitled.png)

## Acknowledgements

This project was developed using the following resources and libraries:
- [IEX Cloud API](https://iexcloud.io/)
- [pandas library](https://pandas.pydata.org/)
- [numpy library](https://numpy.org/)
- [scipy library](https://www.scipy.org/)
- [xlsxwriter library](https://xlsxwriter.readthedocs.io/)
- [matplotlib library](https://matplotlib.org/)
- Special thanks to the creators of the open-source libraries used in this project.
