# Using FinTA for Trading Signals

## Background

In this activity, you’ll use the [FinTA](https://pypi.org/project/finta/) Python library to generate the trading signals that power your trading algorithms.

## Instructions

The instructions for this activity are divided into three sections:

* Prologue: Get Set Up

* Part 1: Re-Create the DMAC trading algorithm by Using Technical Indicators from the FinTA Library

* Create a New Trading Algorithm by Using the Bollinger Bands Technical Indicator from the FinTA Library

### Prologue: Get Set Up

1. If you haven't already installed the [FinTA](https://pypi.org/project/finta/) Python library, open a new terminal window, and then install it as follows:

    * Activate your virtual environment.

    * At the command prompt, type the following command:

      ```shell
      pip install finta
      ```

2. Using the Jupyter notebook that the `Unsolved` folder includes, import the TA module from the FinTA library.

3. Read the `ixn_ohlcv.csv` file from the `Resources` folder into a Pandas DataFrame. Review the DataFrame, and then generate a plot of the "close" price by using hvPlot.

### Part 1: Re-Create the DMAC trading algorithm by Using Technical Indicators from the FinTA Library

Using the [FinTA](https://pypi.org/project/finta/) Python library, reconstruct the simple moving average (`TA.SMA`) dual crossover trading algorithm. To do so, complete the following steps:

1. Set a `short_window` variable to 15 and a `long_window` variable to 50.

2. Using the [FinTA](https://pypi.org/project/finta/) syntax, create two DataFrame columns. One column holds the "Short" simple moving average calculation. The other column holds the "Long" simple moving average value calculation. Review the DataFrame to confirm that the new columns got added.

3. Create a "Signal" column for the DataFrame, and set the initial value to 0.

4. Create the trading algorithm by using the `np.where` function. The values in the "Signal" column should be updated to 1 where the short-value SMA is greater than the long-value SMA. The values in this column should be 0 otherwise.

5. Create an "Entry/Exit" column in the DataFrame by using the `diff` function. The column values should be 1 where the "Signal" column changes from 0 to 1. And, the column values should be &minus;1 where the "Signal" column changes from 1 to 0. Review the updated DataFrame.

6. Review the visualization that plots the entry points, exit points, and short- and long-window moving averages all against the closing price.

7. Update the trading algorithm by incorporating at least one new moving average technical indicator (such as SSM, SSMA, EMA, or DEMA) into your algorithm, and evaluate the results.

### Part 2: Create a New Trading Algorithm by Using the Bollinger Bands Technical Indicator from the FinTA Library

Using the [FinTA](https://pypi.org/project/finta/) Python library, construct a trading algorithm as follows: An entry position is initiated when the closing price is less than the lower Bollinger band (an indicator that the stock is oversold and that the price is likely to trend higher). An exit position is initiated when the closing price is greater than the upper Bollinger band (an indicator that the stock is overbought and that the price is likely to trend lower). To do so, complete the following steps:

1. Create a copy of the original `ixn_df` DataFrame, and save it as a DataFrame named `bb_signals_df`. Review the DataFrame.

2. Create a DataFrame named `bbands_df` by using the FinTA library syntax to create the Bollinger Bands technical indicator. Review the DataFrame.

3. Using the Pandas [concat](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html) function, concatenate the `bb_signals_df` and `bbands_df` DataFrames. Save them as a new version of `bb_signals_df`. Review the concatenated DataFrame.

4. Review the visualization of the `bb_signals_df` DataFrame, including the Bollinger bands.

5. Create a trading algorithm that incorporates the Bollinger Bands technical indicator, as follows:

    * Create a "Signal" column for the `bb_signals_df` DataFrame. Set the initial value to 0.

    * Create a trading algorithm by using the Pandas `iterrows` function. For each row, if the "close" value is less than "BB_LOWER" (indicating an oversold position), update the "Signal" column value to 1 (indicating a trade entry). If the "close" value is greater than "BB_UPPER" (indicating an overbought position), update the "Signal" column value to &minus;1 (indicating a trade exit).

    * Review the DataFrame.

6. Review the visualization that overlays the entry and exit positions, the “close” value, and each of the three Bollinger bands. What do you notice about the entry and exit positions? Given its current status, would this make a viable trading algorithm?

7. Update the trading algorithm so that for each trade cycle, only the first entry position and the first exit position are identified as trading signals. Review the plot to find out if the variable was correctly incorporated.

    **Hint:** Create a variable named `trading signal` that’s initially assigned a value of 0. You should incorporate this trading signal as a conditional in the `if` statement of the trading algorithm. The value should be adjusted to either 1 or 0 when the "Signal" column is updated.

---

© 2021 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
