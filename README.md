# Near-RT-RIC-Benchmark

This Python script performs various operations on a CSV file containing latency samples from a cloud network. It resamples the data to hourly intervals, calculates the mean latency for each hour, and saves the resulting hourly means to a new CSV file.

To begin, the script imports the necessary libraries: pandas and numpy. Pandas is a powerful data manipulation library that efficiently handles large datasets, while numpy provides support for multi-dimensional arrays and matrices in numerical computing.

Next, the script loads the CSV file using pandas' read_csv() function, storing the resulting DataFrame in the variable df_resampled.

To enable resampling of the data to hourly intervals, the script converts the 'Timestamp' column of the DataFrame to datetime type using pandas' to_datetime() function.

The 'Timestamp' column is then set as the index of the DataFrame using the set_index() function, which is necessary for resampling the data to hourly intervals.

Using the groupby() function from pandas, the DataFrame is resampled to hourly intervals. The resulting DataFrame, df_grouped, contains the mean latency for each hour.

Finally, the script saves the resulting DataFrame to a new CSV file using the to_csv() function from pandas.
After that the script reads a CSV file containing latency samples from a cloud network resampled to hourly intervals, fits a non-linear function to the data, and generates a plot showing the original data points and the fitted function for each latency column in the DataFrame. The plot is saved as a PDF and PNG file.

To start, the script imports the necessary libraries: matplotlib, seaborn, scipy, sklearn, and math. Matplotlib provides a wide range of tools for creating visualizations, seaborn offers a high-level interface for statistical graphics, scipy includes algorithms for scientific computing, sklearn provides machine learning tools, and math offers mathematical functions.

Next, the script loads the CSV file using pandas' read_csv() function, storing the resulting DataFrame in the variable df.

To enable fitting of the non-linear function to the data, the script maps the 'Timestamp' column of the DataFrame to specific intervals (3am = 0, 9am = 1, 3pm = 2, 9pm = 3) using a dictionary and pandas' map() function.

The script defines a non-linear function, func, that takes four parameters (a, b, c, and d) and returns the value of a*x^3 + b*x^2 + c*x + d, where x is the input value.

Using the values() function from pandas, the script generates x values from the 'Timestamp' column of the DataFrame.

The script then creates a figure with subplots for each latency column in the DataFrame using matplotlib's subplots() function. The size of the figure is determined by the number of columns in the DataFrame.

For each subplot, the script obtains the y values from the DataFrame, fits the non-linear function to the data using scipy's curve_fit() function, calculates the fitted y values, computes the root mean squared error (RMSE) between the original data and the fitted function, plots the original data points and the fitted function, sets the title and labels, adjusts the x-axis to represent a 24-hour day, and displays the legend.

Finally, the script saves the resulting plot as a PDF and PNG file using matplotlib's savefig() function.