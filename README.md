# Module-3-Alan-Temiryaev


# Assumptions or discoveries that you made during the analysis
"""
# I made the assumption that every day would yield a positive return, but that was not the case.
# For example, on the early and middle dates [2018-01-16] & [2018-02-24], a positive return was achieved.
# However, on the late date [2018-03-26], a positive yield was achieved only when Coinbase Prices were sub
"""


# Summary tables and calculations
# This are the calculations for the early date:
"""
arbitrage_spread_early = coinbase_df['Close'].loc['2018-01-16'] - bitstamp_df['Close'].loc['2018-01-16']
arbitrage_spread_early.describe()

spread_return_early = arbitrage_spread_early[arbitrage_spread_early>0] / bitstamp_df['Close'].loc['2018-01-16']
spread_return_early.dropna()
spread_return_early.describe()

profitable_trades_early = spread_return_early[spread_return_early > .01]
profitable_trades_early.head()

# For the date early in the dataset, calculate the potential profit per trade in dollars 
# Multiply the profitable trades by the cost of the Bitcoin that was purchased
profit_early = profitable_trades_early * bitstamp_df['Close'].loc['2018-01-16']

# Drop any missing values from the profit DataFrame
profit_per_trade_early = profit_early.dropna()

# View the early profit DataFrame
profit_per_trade_early.head()

# Calculate the sum of the potential profits for the early profit per trade DataFrame
# YOUR CODE HERE 
profit_sum_early = profit_per_trade_early.sum()
profit_sum_early

# Use the cumsum function to calculate the cumulative profits over time for the early profit per trade DataFrame
cumulative_profit_early = profit_per_trade_early.cumsum()


"""
# Visualizations
"""
# Create an overlay plot that visualizes the two dataframes over a period of one day early in the dataset. 
# Be sure that the plots include the parameters `legend`, `figsize`, `title`, `color` and `label` 
bitstamp_df['Close'].loc['2018-01-16'].plot(legend=True, figsize=(15, 7), title="Exchange Comparison (Earlier Time Period)", color="blue", label="Bitstamp", ylabel='Price')
coinbase_df['Close'].loc['2018-01-16'].plot(legend=True, figsize=(15, 7), color="orange", label="Coinbase", xlabel='Timestamp')

# Visualize the arbitrage spread from early in the dataset in a box plot
arbitrage_spread_early.plot(kind="box")

# Plot the results for the early profit per trade DataFrame
profit_per_trade_early.plot(figsize=(10, 5), title='Profit Per Trade (Early)', xlabel='Timestamp', color='blue') 

# Plot the cumulative sum of profits for the early profit per trade DataFrame
cumulative_profit_early.plot(figsize=(10, 7), title="Cumulative Sum Profits (Early)")
"""
