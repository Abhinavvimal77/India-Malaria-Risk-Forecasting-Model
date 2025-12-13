# India Malaria Risk Forecasting and Prioritization System

## Project Overview

This project develops a data-driven, two-stage machine learning framework to forecast malaria outbreaks and map vulnerability across districts in India. The goal is to provide public health officials with actionable insights to proactively manage resources, target interventions, and ultimately reduce the burden of malaria.

Instead of reactively responding to outbreaks, this system helps identify *where* and *how severely* future outbreaks are likely to occur, allowing for smarter, more efficient public health strategies.

## Key Objectives Achieved

1.  **District Vulnerability Analysis:** Categorized Indian districts into distinct vulnerability clusters based on socio-economic indicators and health infrastructure.
2.  **Malaria Outbreak Forecasting:** Developed a robust machine learning model to predict the `Total cases` and `Total deaths` for districts for the upcoming year (2025).
3.  **Hotspot Identification:** Generated a prioritized list and a choropleth map highlighting districts with the highest predicted malaria cases for 2025.
4.  **Policy Driver Identification:** Identified the key factors (features) that most influence malaria case predictions, offering insights for policy formulation.

## Methodology

### Stage 1: Vulnerability Mapping (Objective 1)

* **Data:** 2011 Census data (population density, household size, etc.) and public health facility data.
* **Method:** Unsupervised Machine Learning (K-Means Clustering) to group districts into `Vulnerability_Cluster` profiles (e.g., "High-Risk, Underserved", "Moderate-Risk, Adequate Facilities").

### Stage 2: Malaria Case & Death Forecasting (Objective 2)

* **Data:** Historical malaria case and death data (2000-2024), combined with the `Vulnerability_Cluster` and engineered lagged features (e.g., `Cases_Lag_1Y`, `Deaths_Lag_2Y`).
* **Model:** `HistGradientBoostingRegressor` (or `RandomForestRegressor`) for its ability to handle tabular data and capture complex relationships.
* **Tuning:** `RandomizedSearchCV` was used to find optimal hyperparameters, ensuring the model generalizes well to unseen data.
* **Evaluation:** Model performance was assessed using R-squared (R²) and Mean Absolute Error (MAE) on a time-series validated test set (2022-2024).

## Project Structure

The project is organized into several key Jupyter notebooks (or Python scripts if you converted them):

* **`01_Data_Collection_and_Vulnerability_Analysis.ipynb`**: Handles data loading, cleaning, feature engineering for vulnerability, and the K-Means clustering.
* **`02_Time_Series_Feature_Engineering_and_Modeling.ipynb`**: Focuses on creating lagged features, splitting data, training the RandomForest (or HGB) model, and hyperparameter tuning.
* **`03_Forecasting_and_Reporting.ipynb`**: Generates the 2025 predictions, creates summary reports (top N districts), and plots performance metrics.
* **`final_model_training_data.csv`**: The cleaned and prepared dataset used for model training.
* **`final_2025_prediction_report.csv`**: The complete list of 2025 predictions for all districts.
* **`top_10_forecast_2025.csv`**: A filtered list of only the top 10 predicted high-risk districts for 2025.
* **`INDIA_DISTRICTS.geojson`**: The geographical shapefile used for creating the choropleth maps.

## Key Results & Visualizations

*(You can replace these with actual screenshots from your project!)*

### 1. Top 5 High-Risk Districts: 2022-2024 Actuals vs. 2025 Forecast

This plot visualizes the historical trend and the model's prediction for the top 5 districts.
![Top 5 Forecast Plot Example](top_5_forecast_plot_corrected.png) *(Replace with your actual image file name)*

### 2. Policy Driver Report (Feature Importance)

Identifies the most influential factors in predicting malaria cases.
![Feature Importance Plot Example](policy_driver_feature_importance.png) *(Replace with your actual image file name)*

### 3. Malaria Hotspot Forecast Map (2025)

A choropleth map highlighting districts with the highest predicted malaria cases for 2025.
![Choropleth Map Example](malaria_forecast_map_TOP10.png) *(Replace with your actual image file name, e.g., 'malaria_forecast_map_2025.png' for full map)*

### 4. Dhalai District Forecast (Example)

A specific forecast for a high-risk district, showing actuals vs. prediction.
![Dhalai Forecast Bar Chart Example](dhalai_forecast_barchart.png) *(Replace with your actual image file name)*

## How to Replicate / Run This Project

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/YourUsername/YourRepoName.git](https://github.com/YourUsername/YourRepoName.git)
    cd YourRepoName
    ```
2.  **Install Dependencies:**
    It's highly recommended to use a virtual environment.
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn geopandas jupyterlab
    ```
3.  **Download GeoJSON File:**
    * Download `INDIA_DISTRICTS.geojson` from `https://github.com/datta07/INDIAN-SHAPEFILES/blob/main/INDIA/INDIA_DISTRICTS.geojson`
    * Place this file in your project's root directory.
4.  **Execute Notebooks Sequentially:**
    Open the Jupyter notebooks in the following order and run all cells:
    * `01_Data_Collection_and_Vulnerability_Analysis.ipynb`
    * `02_Time_Series_Feature_Engineering_and_Modeling.ipynb`
    * `03_Forecasting_and_Reporting.ipynb`
5.  **Generate Maps:**
    * Ensure `final_2025_prediction_report.csv` and `top_10_forecast_2025.csv` (generated in step 3) are in your root directory.
    * Run the `map_generation.py` script (or the relevant cells in a notebook) to generate the choropleth maps.

## Data Sources

* **Malaria Cases & Deaths:** (Specify your source here, e.g., National Vector Borne Disease Control Programme (NVBDCP), WHO, or other public health records)
* **Socio-economic & Infrastructure Data:** 2011 Census of India, Ministry of Health and Family Welfare (or other relevant sources for facilities data).
* **Geographical Boundaries:** `INDIA_DISTRICTS.geojson` (from datta07/INDIAN-SHAPEFILES GitHub repository).

## Future Enhancements

* Integration of real-time environmental data (rainfall, temperature, humidity).
* Incorporation of mobility data to track disease spread.
* Development of an interactive dashboard (e.g., using Dash or Streamlit).
* Expansion to sub-district level analysis.

## Contributing

Feel free to open issues, submit pull requests, or suggest improvements!




-Abhinav m -  [Abhinavvimal77](https://github.com/Abhinavvimal77) 

---
