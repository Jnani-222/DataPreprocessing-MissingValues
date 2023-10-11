# Data Missing Value Handling in Python

This README file provides an overview of the Python script used to handle missing values in a dataset. The script reads a dataset from an Excel file, explores the data, identifies missing values, and fills them using various strategies.

## Overview

The primary objective of this script is to handle missing values in a dataset containing information about different car types and their owners. The script applies various strategies to fill missing values, ensuring that the dataset is ready for analysis.

## Note

In this script, we've taken a pragmatic approach to handle missing values without extensive data analysis and visualization. Here's why:

- **No Heat Maps or Visualizations**: While heat maps and other visualizations can be powerful tools to explore relationships between columns, we've opted not to use them. This is because we have a basic understanding of the variables in the data and how they are interconnected. Our primary objective is to handle missing values efficiently and not to perform in-depth data analysis or correlation studies.

- **No Univariate Analysis**: We haven't conducted univariate analysis for any variable in this script. Univariate analysis can be valuable for understanding the distribution of individual variables, identifying outliers, and making data-driven decisions. However, our focus here is on addressing missing data, and we're not conducting a comprehensive analysis of the dataset.

We acknowledge that data analysis and visualization can be essential for many data science projects, but in this specific script, we've chosen to emphasize the missing value handling process. Feel free to incorporate visualizations and exploratory analysis in your data projects as per your specific needs and objectives.

## Dependencies

- numpy
- pandas
- matplotlib
- seaborn

Please make sure you have these Python libraries installed to run the script successfully.

## Script Structure

1. Import necessary libraries and suppress warnings:
   - numpy, pandas, matplotlib, seaborn are imported for data manipulation and visualization.

2. Load the dataset:
   - Read the dataset from the "EDA Cars-1.xlsx" file and create a DataFrame.

3. Basic Data Exploration:
   - Examine the dataset by displaying the first few rows and checking for basic information.

4. Checking for Duplicates:
   - Identify and remove duplicate rows from the dataset to ensure data integrity.

5. Checking for Missing Values:
   - Analyze the dataset for missing values and determine which columns have missing data.

6. Filling Missing Values:
   - Fill missing values in the dataset using various strategies.

### Filling Missing POSTAL CODE Values

- Observe that CITY and POSTAL CODE columns are related.
- Identify missing values in the CITY and POSTAL CODE columns.
- Fill missing CITY values based on the known postal codes using a mapping dictionary.
- Manually fill missing POSTAL CODE values for specific rows.

### Filling Missing CITY Values

- Create a mapping dictionary for postal codes to city names.
- Use the mapping dictionary to fill missing CITY values based on postal codes.

### Filling Missing CAR TYPE Values

- Fill missing CAR TYPE values with the mode (most common value) of the CAR TYPE column.

### Filling Missing TRAVEL TIME Values

- Analyze TRAVEL TIME and fill missing values with the median to handle outliers.

### Filling Missing EDUCATION Values

- Fill missing EDUCATION values based on the JOB column and common patterns.

### Filling Missing SEX Values

- Fill missing SEX values based on available data in the EDUCATION column.

### Filling Missing MARITAL STATUS Values

- Fill missing MARITAL STATUS values based on common patterns in the dataset.

### Filling Missing CAR AGE Values

- Fill missing CAR AGE values with the mean (average) of the CAR AGE column.

### Filling Missing MILES CLOCKED Values

- Fill missing MILES CLOCKED values based on CAR TYPE.

### Filling Missing USE Values

- Fill missing USE values based on JOB and available patterns.

### Filling Missing INCOME Values

- Fill missing INCOME values based on available data, including JOB, EDUCATION, and INCOME analysis.

### Filling Remaining Missing Values

- Fill remaining missing EDUCATION, JOB, and USE values using various strategies.

## Saving the Cleaned Dataset

The script saves the cleaned dataset to an Excel file named "EDA_Finished_Cars.xlsx" without the index column.

### Three Files:

1. **EDA Cars-1.xlsx**: This is the original dataset with missing values.
2. **EDA_Cars.ipynb**: The Python script where data exploration and missing value handling are performed.
3. **EDA_Finished_Cars.xlsx**: The final cleaned dataset after handling missing values.

## Running the Script

To run the script successfully, ensure you have the required dependencies installed. Place the "EDA Cars-1.xlsx" file in the same directory as the script. After running the script, the cleaned dataset will be saved in the same directory as "EDA_Finished_Cars.xlsx."

Feel free to modify the script or use the principles outlined here for your own data preprocessing tasks.
