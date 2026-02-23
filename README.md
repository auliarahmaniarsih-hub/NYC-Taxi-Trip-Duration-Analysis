# Large-Scale Transportation Dataset Analysis (NYC Taxi, 1.45M+ Records)

This project analyzes a large real-world transportation dataset to demonstrate data cleaning, validation, workflow building, and operational analytics using SQL and Python.

The goal is not only prediction, but ensuring data reliability and actionable insight generation from messy structured data.

## What This Project Demonstrates

• Handling and validating large structured datasets
• Building repeatable data processing workflows
• Detecting anomalies and inconsistent records
• Performing trend and operational analysis
• Communicating analytical findings clearly

Tools: SQL, Python (Pandas, NumPy), Matplotlib, LightGBM

## Dataset

Public NYC Taxi Trip Duration dataset (Kaggle competition).
Due to file size limits, raw data is not uploaded to the repository.

## Workflow Overview

Data inspection and quality checks (missing values, duplicates, invalid entries)

## Data cleaning and preprocessing

Feature engineering (temporal and distance features)

## Outlier detection and treatment

SQL exploratory analysis and validation queries

Predictive modeling to understand operational drivers

## Key Findings

• Trip distance and pickup time are the main drivers of trip duration
• A small set of features (~8) explains most performance variability
• Outlier handling improves dataset stability and model reliability
• Vendor and passenger patterns show measurable operational differences

## SQL Analysis

A separate SQL workflow analyzes the processed dataset:

Includes:
• Data validation queries
• Aggregations and grouping analysis
• Vendor comparison
• Passenger behavior patterns
• Performance optimization using indexing

This demonstrates the ability to analyze data without relying only on Python tools.

## Why This Matters

This project focuses on data quality, monitoring, and operational insight, which are critical for analytics and AI training pipelines where inaccurate data directly impacts results.

## How to Run

Install dependencies: pip install -r requirements.txt

Run NYC_Taxi_Trip_Duration.ipynb

Optional: execute sql_analysis.sql in MySQL for SQL analysis
