# Motor Vehicle Collisions - NYC Dataset

This repository contains data on motor vehicle collisions in New York City, sourced from [Data.gov](https://catalog.data.gov/dataset/motor-vehicle-collisions-crashes). The dataset provides information on crash locations, vehicles involved, contributing factors, and outcomes, such as injuries and fatalities. This project focuses on performing Exploratory Data Analysis (EDA) and applying predictive analytics to identify trends and insights regarding vehicle collisions in NYC.

## Dataset Overview

The dataset includes various features, such as:
- **Date and Time**: When the collision occurred.
- **Location**: The incident's Borough, latitude, and longitude.
- **Involved Parties**: Number of persons, pedestrians, cyclists, and motorists involved.
- **Contributing Factors**: Factors like driver inattention, unsafe speed, or vehicle failure.
- **Injuries and Fatalities**: Count of people injured or killed.
- **Vehicles**: Types of vehicles involved in the collision.

## Project Objectives

1. **Exploratory Data Analysis (EDA)**:
    - Clean and preprocess the data to handle missing or inconsistent entries.
    - Visualize data to uncover trends, patterns, and correlations (e.g., heatmaps, bar charts).
    - Identify high-risk areas, times, or conditions for vehicle collisions.
    - Explore the impact of different contributing factors on collision outcomes.

2. **Predictive Analytics**:
    - Build machine learning models to predict a collision's likelihood of injuries or fatalities based on location, time, and contributing factors.
    - Evaluate the model performance using accuracy, precision, recall, and other relevant metrics.
    - Use the models to suggest preventive measures or insights for improving traffic safety.

## Tools & Technologies

- **Languages**: Python
- **Libraries**:
  - Data Analysis: `pandas`, `numpy`
  - Data Visualization: `matplotlib`, `seaborn`, `plotly`
  - Machine Learning: `scikit-learn`
- **Jupyter Notebooks**: For data exploration and modeling.

## Installation & Setup

To run the analysis locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/nyc-motor-vehicle-collisions.git
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
   - Handle missing values.
   - Correct data types for date and time fields.
   - Feature engineering, such as encoding categorical variables.

2. **Exploratory Data Analysis (EDA)**:
   - Time-based analysis: Identify trends across different times of day, days of the week, and seasons.
   - Location-based analysis: Map collision hotspots in NYC.
   - Factor-based analysis: Investigate the most common contributing factors to collisions.

3. **Predictive Modeling**:
   - Train models (e.g., Decision Trees, Random Forest, Logistic Regression) to predict the severity of collisions.
   - Fine-tune model parameters and evaluate performance.
   
## Visualizations

- **Heatmaps**: To identify geographic collision hotspots.
- **Bar Charts**: To compare collision rates by borough, vehicle type, or contributing factors.
- **Time-Series Analysis**: To track trends over time.
  
## Contributing

Contributions are welcome! If you'd like to contribute to this project, please fork the repository and create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
