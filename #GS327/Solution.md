## Google Cloud Data Engineering Challenge Lab #GS327

This repository contains solutions for the Google Cloud Data Engineering Challenge Lab #GS327. The challenge focuses on data engineering tasks using Google Cloud Platform (GCP).

## Task 1: Clean Your Training Data

To clean the training data and create a new table, run the following SQL query:

```sql
CREATE OR REPLACE TABLE taxirides.taxi_training_data_474 AS 
SELECT
  (tolls_amount + fare_amount) AS fare_amount_138,
  pickup_datetime,
  pickup_longitude AS pickuplon,
  pickup_latitude AS pickuplat,
  dropoff_longitude AS dropofflon,
  dropoff_latitude AS dropofflat,
  passenger_count AS passengers,
FROM
  taxirides.historical_taxi_rides_raw
WHERE
  RAND() < 0.001
  AND trip_distance > 4
  AND fare_amount >= 2.0
  AND pickup_longitude > -78
  AND pickup_longitude < -70;
```

## Task 2: Create a BigQuery ML Model

To create a BigQuery ML model for fare prediction, execute the following SQL query:

```sql
CREATE OR REPLACE MODEL taxirides.fare_model_551
TRANSFORM(
  * EXCEPT(pickup_datetime),
  ST_Distance(ST_GeogPoint(pickuplon, pickuplat), ST_GeogPoint(dropofflon, dropofflat)) AS euclidean,
  CAST(EXTRACT(DAYOFWEEK FROM pickup_datetime) AS STRING) AS dayofweek,
  CAST(EXTRACT(HOUR FROM pickup_datetime) AS STRING) AS hourofday
)
OPTIONS(input_label_cols=['fare_amount_138'], model_type='linear_reg')
AS
SELECT * FROM taxirides.taxi_training_data_474;
```

## Task 3: Perform Batch Prediction on New Data

To perform batch predictions on new data, create a table for the predictions using the following SQL query:

```sql
CREATE OR REPLACE TABLE taxirides.2015_fare_amount_predictions
AS
SELECT * FROM ML.PREDICT(MODEL taxirides.fare_model_551, (SELECT * FROM taxirides.report_prediction_data));
```

## Repository Structure

- `task1.sql`: SQL query for Task 1.
- `task2.sql`: SQL query for Task 2.
- `task3.sql`: SQL query for Task 3.
- `solution.md`: This file, providing an overview of the challenge and SQL solutions.

You can execute these SQL queries in your Google BigQuery environment to complete the tasks.

Good luck with your Google Cloud Data Engineering Challenge Lab #GS327!
```
