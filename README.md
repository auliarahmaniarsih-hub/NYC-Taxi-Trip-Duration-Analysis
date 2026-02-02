# NYC Taxi Trip Duration Prediction

This project builds a machine learning model to predict taxi trip duration in New York City.
The workflow covers data understanding, preprocessing, feature engineering, outlier handling, model training with LightGBM, hyperparameter tuning and performance evaluation.

## Data Loading and Initial Inspection

The dataset was loaded and inspected to understand it's structure, feature types, and overall quality.
Initial checks included reviewing the number of rows and columns, data types, summary statistic, missing values, and duplicate records to ensure data consistency before modeling.

## Feature Engineering

Several feature engineering techniques were applied to enrich the dataset:

### Target Transformation
- Applied log1p transformation to the target variable ('trip_duration') to reduce right skewness and stabilize model training.

### Temporal Features
- Extracted hour of day, day of week, and month from pick up datetime to capture time-based travel patterns.

### Spatial and Distance Features
- Computed multiple distance metrics between pickup and dropoff location:
    - Haversine distance (great-circle distance)
    - Manhattan distance
    - Euclidean distance
- Created latitude and longitude difference features to capture directional movement.

### Speed Feature
- Estimated average trip speed (km/h) using haversine distance and trip duration.
- Handled infinite and invalid values to maintain data integrity.

## Correlation Analysis

A correlation matrix heatmap was generated using numerical features to examine linear relationship between variable and identify potential multicollinearity among engineered features.

## Data Sampling

Due to the large size of the dataset, a random sample of 100,000 observation was selected to improve computational efficiency while preserving the overall data distribution.

## Outlier Detection

Outliers were detected using the Isolation Forest algorithm on scaled numerical features.
RobustScaler was applied to reduce the influence of extreme values during outlier detection.

Outliers were visually inspected using scatter plots of distance-based features against average speed, and boxplots were used to confirm the presence of extreme values.
This step validated the Isolation Forest results and guided the decision to cap outliers rather than remove them.


## Outlier Visualization

Outliers were visually inspected using scatter plots comparing distance-based features against average trip speed, and boxplots were used to visualize the distribution of distance-based features and confirm the presence of extreme values identified during outlier detection.
This step helped validate the Isolation Forest results, provided interpretability for detected anomalies, and guide the decision to apply capping rather than removing observation.

## Outlier Treatment

Outliers were handled using an IQR-based capping (winsorization) to limit their influence while preserving all data points.

Distance-based and spatial features were capped using statistically defined bounds.
Boxplots and histograms were used to verify that the distributions were improved after capping.

## Dropping Unnecessary Columns

Uninformative identifier columns and redundant timestamp fields were removed prior to modeling.

## Categorical Encoding

Categorical features were encoded using label encoding, which is compatible with LightGBM's tree-based architecture and avoids the dimensionality increase of one-hot encoding.

## Modeling Section

A LightGBM Regressor was trained to predict log-transformed trip duration using engineered spatial, temporal, and distance-based features.

Regularization and subsampling techniques were applied to reduce overfitting, including:
- Controlled tree depth and number of leaves
- L1 and L2 regularization
- Feature and row subsampling

The trained model was evaluated using a train-validation split to assess generalization performance.
Performance metrics included R², RMSE, and MAE.

## Feature Importance Analysis

Feature importance analysis identified the most influential predictors.
Distance-based and temporal features were the strongest contributors.
Cumulative importance analysis showed that approximately 8 features captured 80% of the total model importance.

## Model Insights

Distance-based and temporal features were the strongest predictors of taxi trip duration.
Cumulative importance analysis indicated that approximately 8 features captured 80% of the total model importance.

## Cross Validation and Hyperparameter Tuning

To assess model stability and generalization, 5-fold cross-validation was performed using R² as the metric, showing consistent performance across folds.

GridSearchCV was used to tune key LightGBM hyperparameters, including learning rate, tree complexity, and regularization terms.
A smaller grid and fewer estimators were used to balance computational efficiency with model performance.

The optimized LightGBM model was then retrained on the full dataset using the best hyperparameters, resulting in improved validation performance.

## Final Evaluation Metrics

The final model was evaluated using multiple regression metrics, including R², RMSE, and MAE, providing a comprehensive assessment of predictive performance.

## Key Takeaways
- Temporal and distance-based features are the strongest predictors of NYC taxi trip duration.
- Outlier handling via capping preserves data while improving model stability.
- LightGBM with hyperparameter tuning provides accurate and efficient predictions on large datasets.

## How to Run
1. Install dependencies: `pip install -r requirements.txt`
2. Run `NYC_Taxi_Trip_Duration.ipynb` from start to finish.
3. The final trained model and plots will be generated automatically.
