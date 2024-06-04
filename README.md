# Car Accident Contributory Cause Classification in Chicago

![CPD image](CPD.jpg)

## Introduction

Car accidents are a significant public safety issue, and understanding their causes is crucial for implementing effective prevention strategies. This project aims to build a classifier that predicts the primary contributory cause of car accidents in Chicago using data on the people involved, the vehicles, and the crash conditions. The insights from this model can help the Vehicle Safety Board and the City of Chicago identify key factors contributing to accidents and take preventive measures to enhance road safety.

## Business Understanding

### Overview

The primary goal of this project is to build a classifier that predicts the primary contributory cause of car accidents in Chicago. The target audience includes the Vehicle Safety Board and the City of Chicago, who are interested in reducing traffic accidents and uncovering patterns that lead to accidents.

### Challenges

1. **Data Complexity**: The datasets include a wide range of information about people, vehicles, and accidents, making data cleaning and preprocessing challenging.
2. **Class Imbalance**: Some primary contributory causes have very few samples, leading to potential class imbalance issues.
3. **Feature Engineering**: Identifying the most relevant features from a large number of variables requires careful analysis and domain knowledge.

### Proposed Solution

- **Metrics**: The primary metric for evaluating the model will be the accuracy score, with a target accuracy of 80%.
- **Other Metrics**: We will also consider precision, recall, and F1 score to get a comprehensive understanding of model performance.

### Brief Conclusion

By building a reliable classifier, we can help the City of Chicago and the Vehicle Safety Board identify key factors contributing to car accidents and take preventive measures to enhance road safety.

### Problem Statement

The goal of this project is to develop a classification model that predicts the primary contributory cause of car accidents in Chicago using data about the people involved, the vehicles, and the crash conditions. This model will help stakeholders understand the factors leading to accidents and implement measures to reduce their occurrence.

### Objectives

1. **Data Collection**: Gather and combine datasets related to traffic crashes, people involved, and vehicles.
2. **Data Cleaning and Preparation**: Handle missing values, duplicates, and outliers. Perform necessary data transformations.
3. **Exploratory Data Analysis (EDA)**: Conduct univariate and bivariate analysis to understand the data distribution and relationships.
4. **Modeling**: Build and evaluate multiple classification models, starting with a baseline model and progressing to more complex models.
5. **Evaluation**: Assess model performance using metrics such as accuracy, precision, recall, and F1 score.
6. **Recommendations**: Provide actionable insights and recommendations based on the model's findings.

## Data Understanding

### Sources

The datasets used in this project are:
1. **People Dataset**: Information about people involved in crashes.
2. **Vehicle Dataset**: Information about vehicles involved in crashes.

Both datasets are available for download from the Chicago Data Portal.

## Data Preparation

In this section, we merge the People and Vehicle datasets based on the `CRASH_RECORD_ID` column. This will allow us to combine information about people involved in crashes with information about the vehicles involved.

```python
# Load the People dataset in chunks to avoid errors when loading due to data size.
chunk_size = 50000
chunks = pd.read_csv('Traffic_Crashes_-_People_20240531.csv', chunksize=chunk_size)

# Initialize an empty list to store the chunks
people_chunks = []

# Iterate over the chunks and append them to the list
for chunk in chunks:
    people_chunks.append(chunk)

# Concatenate the chunks to create the full People dataset
people_data = pd.concat(people_chunks, ignore_index=True)

# Display the first few rows of the People dataset
people_data.head()

# Loading the vehicle dataset and display.
vehicle_data = pd.read_csv('Traffic_Crashes_-_Vehicles_20240531.csv')
vehicle_data.head()
