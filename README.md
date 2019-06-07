# Grab AI for S.E.A. challenge
## Safety
Given the telematics data for each trip and the label if the trip is tagged as dangerous driving, derive a model that can detect dangerous driving trips.

## How to reproduce the results
1. Change path and create required folders.
2. Run `process_data.ipynb` to merge all entries into a single dataframe. Save holdout set to `test`
3. Run `preprocess.ipynb` to generate features and aggregate all features based on `bookingID`. Save holdout set to `agg_test`
4. Run `model.ipynb` to generate predictions.