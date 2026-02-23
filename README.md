# Large-Scale Transportation Dataset Analysis (NYC Taxi, 1.45M+ Records)

This project analyzes a real-world transportation dataset to demonstrate end-to-end data handling — from raw data validation and preparation to operational insight generation and anomaly detection using SQL and Python.

The objective is not only building a predictive model, but ensuring data reliability, monitoring dataset behavior, and extracting actionable operational insights from imperfect structured data.

## What This Project Demonstrates

Handling and validating large structured datasets (1.45M+ records)

Building repeatable data processing workflows

Detecting anomalies and inconsistent records

Performing trend and operational analysis

Translating analytical results into business-readable insights

Tools: SQL, Python (Pandas, NumPy), Matplotlib, LightGBM

## Dataset

Public NYC Taxi Trip Duration dataset from Kaggle.
(Raw files are excluded due to GitHub size limitations.)

## Workflow Overview
1. Data Inspection & Quality Checks

Missing value detection

Duplicate record checks

Invalid coordinate and duration validation

Dataset consistency verification

2. Data Cleaning & Preprocessing

Structured data preparation

Data type corrections

Handling invalid and infinite values

3. Feature Engineering

Temporal features (hour, weekday, month)

Spatial features (pickup/dropoff coordinates)

Distance metrics (Haversine, Manhattan, Euclidean)

4. Outlier Detection & Treatment

Isolation Forest anomaly detection

Visual validation using scatterplots and boxplots

IQR-based capping (winsorization) to preserve records while stabilizing distribution

5. SQL Exploratory & Validation Analysis

Aggregations and grouping analysis

Vendor performance comparison

Passenger behavior patterns

Indexed queries for performance optimization

6. Predictive Modeling

A LightGBM regression model estimates expected trip duration based on operational factors such as time and distance.

The model is used primarily for understanding operational behavior, not just prediction.

Unusual Trip Detection (Operational Anomaly Detection)

The prediction model is extended to identify unusual taxi trips.

Predicted trip duration is converted back into seconds for interpretability.
Trips are evaluated using residual analysis:

Residual = Actual Duration − Expected Duration

Trips with large deviations from expected behavior are flagged as unusual.

This allows the model to function as a data monitoring and validation tool, not only a forecasting model.

## Practical Uses

Detect abnormal service behavior

Identify possible data recording issues

Monitor operational inconsistencies

Support data quality control processes

## Key Findings

Trip distance and pickup time are primary drivers of trip duration

Approximately 8 features explain most performance variability

Outlier handling improves dataset stability and model performance

Vendor and passenger patterns show measurable operational differences

## Why This Matters

Analytics and machine learning systems depend heavily on data quality.
Unreliable data leads to unreliable models and inaccurate reporting.

This project demonstrates how analytics can be used to:

Monitor dataset reliability

Validate operational data

Detect anomalies early

Support trustworthy reporting pipelines

## SQL Analysis

A separate SQL workflow analyzes the processed dataset without relying on Python.

Includes:

Data validation queries

Aggregation analysis

Vendor comparison

Passenger pattern analysis

Query optimization using indexing

This highlights the ability to perform analytical work directly in databases, a core skill in real data analyst roles.

How to Run

## Install dependencies:

pip install -r requirements.txt

Run:

NYC_Taxi_Trip_Duration.ipynb

Optional:
Run sql_analysis.sql in MySQL to reproduce the SQL analysis.
