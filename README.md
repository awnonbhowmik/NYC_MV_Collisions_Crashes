# Motor Vehicle Collisions - NYC Dataset

This repository contains data on motor vehicle collisions in New York City (sourced from [Data.gov](https://catalog.data.gov/dataset/motor-vehicle-collisions-crashes).), focused on information such as crash dates, times, and details on injuries and fatalities among pedestrians, cyclists, and motorists. This project leverages Exploratory Data Analysis (EDA) to reveal patterns in collisions and applies predictive analytics to forecast high-risk periods and factors contributing to injuries and fatalities.

## Project Overview
This project involves using a Negative Binomial Model and LSTM neural network to predict counts of injuries and fatalities. It includes data preprocessing, model building, evaluation, and visualization.

## Dataset Overview

The dataset includes various features, such as:
- **Date and Time**: Specific date and time of the crash.
- **Injuries and Fatalities**: Total count of injured or killed individuals, including breakdowns for pedestrians, cyclists, and motorists.
- **Categorical Time Intervals**: Defined intervals such as Morning Commute, School Hours, and Evening for detailed analysis.
  
## Project Objectives

1. **Exploratory Data Analysis (EDA)**:
   - Clean and preprocess data for consistency.
   - Visualize data to understand trends, patterns, and correlations.
   - Identify high-risk time intervals, such as Morning Commute or School Hours, for crashes.
   - Analyze the impact of time and location on injuries and fatalities.

2. **Predictive Analytics**:
   - Build machine learning models to predict the likelihood of injuries or fatalities based on time intervals and contributing factors.
   - Evaluate models using performance metrics such as accuracy, precision, and recall.
   - Use model insights to suggest preventive measures to enhance road safety in NYC.

## Notebook Summary
- **Data Processing:** Loaded data features such as year and population, scaled the features, and set target variables for prediction.
- **Modeling:** Built separate neural network models for predicting injuries and fatalities, using layers and activation functions suitable for regression.
- **Evaluation:** Evaluated model performance with loss metrics and RMSE.
- **Visualization:** Included loss curve plots for training and validation, along with prediction visualizations.

## Tools & Technologies

- **Languages**: Python
- **Libraries**:
   - Data Analysis: `pandas`, `numpy`
   - Data Visualization: `matplotlib`, `seaborn`, `plotly`
   - Machine Learning: `scikit-learn`
- **Jupyter Notebooks**: For data exploration, EDA, and predictive modeling.

## Installation & Setup

To run the analysis locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/NYC_MV_Collisions_Crashes.git
    ```
2. Create and activate a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate   # For Windows: venv\Scripts\activate
    ```
3. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
4. Launch Jupyter Notebook:
    ```bash
    jupyter notebook
    ```

## EDA & Predictive Analytics Workflow

1. **Data Preprocessing**:
   - Handle missing or inconsistent entries.
   - Convert date and time fields to appropriate formats.
   - Apply categorical encoding for time intervals (e.g., Morning Commute, School Hours).

2. **Exploratory Data Analysis (EDA)**:
   - **Time-based Analysis**: Examine trends across daily activity intervals, days of the week, and seasonal trends.
   - **Injury Analysis**: Explore injury and fatality rates among pedestrians, cyclists, and motorists.
   - **Population-Based Insights**: Adjust trends based on NYC population over time for context.

3. **Predictive Modeling**:
   - Train models (e.g., Decision Trees, Random Forest, Logistic Regression) to predict the severity of collisions.
   - Fine-tune parameters and assess model performance.
   
## Visualizations

- **Time Interval Charts**: Compare injuries and fatalities across time intervals, such as School Hours and Commute periods.
- **Injury Breakdown Charts**: Visualize injuries across different groups (e.g., pedestrians, cyclists, motorists).
- **Time-Series Analysis**: Track trends in crash outcomes over the years.



All Rights Reserved ©
