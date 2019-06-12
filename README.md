## Executive summary
### Process data
First, I merged all sessions and `csv` files for features into a single `dataframe`. For each `bookingID` that has labels of both `safe` and `dangerous`, I removed the `safe` label.
### Preprocessing
I started by removing outliers from the dataset. Using `acceleration` and `gyro` features, I did some feature-engineering to come up with features such as `pitch`, `roll`, and others. I then took the summary statistics of each feature, such as the `min` and `max` of each feature. I then merged the summary statistics `dataframe` with its respective label.
### Model
I tried running 3 models, starting with `lightgbm`. The highest AUC-ROC for an out-of-fold validation strategy is 0.6927. `gam` and `xgboost` resulted in a lower AUC-ROC.

## How to generate predictions
0. Download `notebooks` folder.
1. Change path and create required folders based on `0-process_data.ipynb`
2. Run `0-process_data.ipynb` to merge all entries into a single dataframe. Save holdout set to `test`.
3. Run `1-preprocess.ipynb` and uncomment lines with `UNCOMMENT` for holdout set to generate features and aggregate all features based on `bookingID`. Save holdout set to `agg_test`.
4. Run `2-model.ipynb` and uncomment lines with `UNCOMMENT` for holdout set to generate predictions.

## Important takeaways
0. A feature importance plot can be found at `plots` folder. Some of the most important features to determine whether is a trip safe or dangerous are `Speed_max`, `acceleration_y_mean_abs_change`, `acceleration_z_kurtosis` and others.
1. There is a "leaked" feature `max_second`, which is the maximum second of each `bookingID`. Adding this feature boosts the AUC-ROC from 0.68 to 0.72. I personally think that this feature has little value from the business or practical point of view if Grab were to deploy the model.
