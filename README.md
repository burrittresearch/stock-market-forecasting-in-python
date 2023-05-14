# stock-market-forecasting-in-python
This notebook includes coding and notes for predicting prices of financial market assets including stocks, indices, and ETFs. Using a single class object and a variety of concise methods, users can get financial asset information, clean and explore data, model prices using classification and regression algorithms, and get a robust set of evaluation reports and visualizations.

## Highlights

### Efficient Work
Users can select an asset like the NASDAQ Composite (^IXIC), download data based on a variety of available time periods (durations) and time intervals. The raw dataframes can then be explored and visualized to help in the feature selection process. From there, data can be cleaned, split tested, modeled, and evaluated for precision. The processes are all available as independent methods so that work can be completed efficiently.
 
### Modeling Using Classification and Regression Algorithms
Random forest classification and multiple linear regression have their own methods and can be run independently. The training and test sets are manually split based on time to avoid leakage.
 
For the classification algorithm, the target (dependent) variable is defined by the change in price from one period to the next. If the asset goes up, it is given a 1 label. If it goes down, it is given a 0 label. The model is then run comparing predicted classifications with actual classifications from the test set. For the regression algorithm, the target (dependent) variable is defined as the next period's price. The model is then run comparing predicted prices with actual prices from the test set.
 
The models are evaluated based on a variety of measures. For classification the measures include accuracy score, f1 score, precision score, and score. For regression the measures include score, f2 score, and mean squared error. The measures are summarized, printed and visualized.
 
For the classification algorithm, additional reports and visualizations include a classification report, crosstab confusion matrix, and a confusion matrix heatmap. For the regression algorithm additional visualizations include a comparison line plot of actual and predicted results of the test set.

For both algorithms, predicted and actual results are output to a comparison dataframe and printed and visualized. 

### Loop Through Intervals

Because of the time-driven nature of market assets, three different time intervals are used when running the models. The default time intervals are one day ('1d'), one week ('1wk'), and one month ('1mo'). The models are run and looped through these different intervals, which can be adjusted by the user. The default time period (duration) is the maximum available data ('max'), which can also be adjusted by the user.

### Model Results on Nasdaq and IBM Prices

The notebook includes results from the models run on two assets, the NASDAQ composite ('^IXIC') and IBM ('ibm'). For both assets the default intervals ('1d', '1wk', '1mo') and the default time period ('max') were used.
For the classification model, the NASDAQ accuracy scores ranged from 0.35 to 0.47, which indicated the model worked below average. For IBM precision scores ranged from 0.50 to 0.52, which indicated the model below average.
For the regression model, the NASDAQ r2 scores ranged from 0.98 to 0.99, which indicated the model worked well. For IBM r2 scores ranged from 0.91 to 0.95, which indicated the model worked well.

### Available Methods

get_ticker

Returns the asset ticker.

get_period

Returns the data time duration.

get_interval

Returns the data time interval.

download_csv

Downloads the data to a local csv file. First, checks to see if file exists at default google drive location. Then looks to __init__ method for update. If file already exists and update argument is False, then existing file is not updated. If File already exists and update argument is True, then existing file is updated. If file doesn't exist, it is downloaded. Prints message indicating operations that were performed.

get_raw_dataframes

Runs download_csv to check if file exists, needs updating, doesn't need updating, or needs downloading. Then creates dataframe from csv and performs basic cleaning processes. Returns the raw dataframe.

explore_raw_dataframes

Runs get_raw_dataframe and then prints basic dataframe information.

get_clean_dataframes

Runs get_raw_dataframe and then performs more advanced cleaning processes to prepare data from modeling. These include dropping unwanted features, renaming others, and creating price targets for classification and regression algorithms.
 
get_visual_data

Runs get_clean_dataframes to prepare data. Then creates visualizations for optimizing feature selection including asset price line plot, feature correlation heatmap, and feature and target pairplots, histograms, and regplots.

run_class_model

Runs get_clean_dataframes to prepare data. Then splits data and runs random forest classification algorithm for intervals passed by tpl_model_intervals. By default, print classification report, crosstab confusion matrix, and confusion matrix heatmap (bool_get_reports) and dataframes (bool_get_dfs) for each modeled interval. Then summarizes results of all model runs and prints dataframe and visualization.

run_class_model_list

Runs run_class_model for a tuple of asset tickers.

run_class_model

Runs get_clean_dataframes to prepare data. Then splits data and runs random forest classification algorithm for intervals passed by tpl_model_intervals. By default, prints various evaluation reports (bool_get_reports) and dataframes (bool_get_dfs) for each modeled interval. Then summarizes results of all model runs and prints dataframe and visualization.

run_class_model_list

Runs run_class_model for a tuple of asset tickers.

run_mlr_model

Runs get_clean_dataframes to prepare data. Then splits data and runs multiple linear regression algorithm for intervals passed by tpl_model_intervals. By default, prints model coefficients, model intercepts, line plot (bool_get_reports) and dataframes (bool_get_dfs) for each modeled interval. Then summarizes results of all model runs and prints dataframe and visualization.

run_mlr_model_list

Runs run_mlr_model for a tuple of asset tickers.

#### Raw Data Source

Raw data is downloaded using the [yfinance module]('https://pypi.org/project/yfinance'), which gets its data from yahoo finance.


