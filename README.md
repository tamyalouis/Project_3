# Project_3

# Health Data Analysis Project

## Project Overview
This project aims to analyze the impact of proximity to preventive health care services and hospital locations on hospitalization rates for individuals of various demographic strata managing diabetes and heart disease in the state of Colorado. 

## Objective
- Identify patterns in healthcare access by analyzing socioeconomic and health outcome data.
- Evaluate potential healthcare accessibility gaps at the county level.
- Visualize healthcare facility distribution using geographic data.

## Datasets Used
1. **Socioeconomic Indicators Dataset**  
   - Population statistics, income, and density data for various counties in Colorado.
   - Source: CDPHE (Colorado Department of Public Health and Environment): https://data-cdphe.opendata.arcgis.com/ 
   
2. **Health Facilities Dataset**  
   - Locations and types of healthcare facilities (e.g., hospitals, clinics).
   - Source: CDPHE (Colorado Department of Public Health and Environment): https://data-cdphe.opendata.arcgis.com/

3. **Health Outcomes Dataset**  
   - Data related to health conditions such as diabetes and heart disease rates.
   - Source: CDPHE (Colorado Department of Public Health and Environment): https://data-cdphe.opendata.arcgis.com/

# ETL Process Overview

This project follows the ETL (Extract, Transform, Load) workflow to process and analyze the data.

## 1. Extract
- Data is sourced from public datasets in CSV format.

## 2. Transform
- **Data Cleaning:** 
  - Standardized column names.
  - Handled missing values by filling with `0` or appropriate replacements.
  - Filtered records to include only hospitals from the facilities dataset.

- **Data Merging:** 
  - Combined socioeconomic indicators, health outcomes, and facilities data on the `county` field.

- **Feature Engineering:** 
  - Created a population density category (Low, Medium, High).

## 3. Load
- The transformed data was stored in an SQLite database using SQLAlchemy.
- Data can be queried using SQL commands for further analysis.

# Database Design

## Database Choice: SQLite

We chose SQLite because:
- It is lightweight and does not require server installation.
- It provides efficient storage and querying capabilities for our analysis.

### Tables and Schema

Table: `health_data`
- `county` (TEXT) - Name of the county.
- `population_total` (INTEGER) - Total population in the county.
- `population_density_persqmi` (FLOAT) - Population density per square mile.
- `diabetes_adjrate` (FLOAT) - Adjusted diabetes hospitalization rate.
- `facility_type` (TEXT) - Type of healthcare facility.
- `latitude` (FLOAT) - Facility latitude.
- `longitude` (FLOAT) - Facility longitude.

# Ethical Considerations

When working with healthcare data, it's important to ensure responsible handling and compliance with ethical standards.

1. **Data Privacy:**  
   - The data used in this analysis is publicly available and does not contain personally identifiable information (PII) or protected health information (PHI).

2. **Bias Mitigation:**  
   - The analysis avoids reinforcing existing healthcare disparities.
   - Care is taken to ensure data represents diverse populations accurately.

3. **Transparency:**  
   - All data sources and transformation processes are documented for clarity and reproducibility.

4. **Usage Guidelines:**  
   - The insights derived from this analysis should be used for informational purposes only and not for medical or policy decision-making.
   
# How to Use the Project

## Prerequisites
Ensure you have the following installed:
- **Python 3.x**
- **Jupyter Notebook**
- **Required Python libraries:** `pandas`, `sqlalchemy`, `folium`, `matplotlib`

Install dependencies using:

```
pip install pandas sqlalchemy matplotlib folium
```

## Steps to Run the Project

1. Clone the GitHub repository:  
   [Project Repository](https://github.com/tamyalouis/Project_3.git)

2. Navigate to the project directory and launch Jupyter Notebook:  
   ```
   jupyter notebook
   ```
- Load data.
- Transform and store data in SQLite.
- Generate insights and visualizations.

## Viewing the Database
You can view the stored SQLite database using:

- **SQLite CLI:**
Open the database using the following command:
```
sqlite3 health_data.db
```
- **DB Browser for SQLite:**  
[Download here](https://sqlitebrowser.org/)