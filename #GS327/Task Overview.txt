# Google Cloud Data Engineering Challenge Lab #GS327

This repository contains solutions and resources for the Google Cloud Data Engineering Challenge Lab #GS327.

## Overview

In this challenge, you will perform various tasks related to data engineering and machine learning using Google Cloud Platform (GCP). The tasks include data cleaning, building a BigQuery ML model, and performing batch predictions on new data.

## Tasks

### Task 1: Clean Your Training Data

- Create a clean copy of the historical taxi rides data and store it in the `taxi_training_data_474` table.
- Clean the data by ensuring trip distance is greater than 4, removing rows with small fare amounts, validating latitude and longitude, and more.

### Task 2: Create a BigQuery ML Model

- Build a BigQuery ML model named `fare_model_551` using the cleaned training data.
- The model should predict `fare_amount_138`, and it should achieve an RMSE of 10 or less.

### Task 3: Perform Batch Prediction on New Data

- Use the `fare_model_551` to predict `fare_amount_138` on new data from `report_prediction_data`.
- Store the prediction results in a table named `2015_fare_amount_predictions`.

## Repository Structure

- Task 1 Solution: Contains scripts and documentation for data cleaning.
- Task 2 Solution: Contains BigQuery SQL queries and model creation details.
- Task 3 Solution: Includes instructions and code for batch predictions.
- README.md: This file, providing an overview of the challenge and tasks.

## Getting Started

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your-username/gcp-challenge-lab-gs327.git
