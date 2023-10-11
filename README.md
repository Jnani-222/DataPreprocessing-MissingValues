# Data Missing Value Handling in Python

This README file provides an overview of the Python script used to handle missing values in a dataset. The script reads a dataset from an Excel file, explores the data, identifies missing values, and fills them using various strategies.

## Overview

The primary objective of this script is to handle missing values in a dataset containing information about different car types and their owners. The script applies various strategies to fill missing values, ensuring that the dataset is ready for analysis.
Provided a dataset with various columns representing different attributes or features. Here's a brief description of the columns:

1. INDEX: A unique identifier for each entry.
2. INCOME: The income of the individual.
3. MARITAL STATUS: The marital status of the individual (e.g., "Yes" or "No").
4. SEX: The gender of the individual (e.g., "M" for male, "F" for female).
5. EDUCATION: The highest level of education attained by the individual (e.g., "Bachelors," "High School," "Masters," etc.).
6. JOB: The occupation or job category of the individual.
7. TRAVEL TIME: Time spent traveling (in minutes).
8. USE: The purpose of the car's use (e.g., "Commercial," "Private").
9. MILES CLOCKED: The number of miles driven.
10. CAR TYPE: The type of car (e.g., "Sports Car," "SUV," "Minivan," etc.).
11. CAR AGE: The age of the car in years.
12. CITY: The city where the individual resides.
13. POSTAL CODE: The postal code of the individual's location.

## Note

### Handling Missing Values

In this project, I adopt a pragmatic approach for handling missing values, taking into consideration the data type of the variable and its potential dependencies on other columns. Here's our general strategy:

### Numerical Variables

For missing values in numerical variables:
1. **Outlier Detection**: I begin by checking for outliers in the given numerical column using statistical methods or domain knowledge. If significant outliers are present, I choose to fill missing values with the **median** of the respective column. The median is robust to outliers and can provide a representative central tendency.
2. **No Outliers**: In cases where no significant outliers are detected, I opt to fill missing values with the **mean** of the respective column. The mean is a suitable measure for central tendency when outliers are not a concern.

### Categorical Variables

For missing values in categorical variables:
1. I fill missing values with the **mode** (the most frequent category) of the respective column.

### Dependency Consideration

I also recognize that the choice of how to fill missing values may be influenced by the specific dataset and its dependencies. In some cases, the missing value strategy may vary based on the relationship betIen columns. It is advisable to perform exploratory data analysis and statistical tests to assess such dependencies, which may influence the choice betIen mean, median, or mode for filling missing values.

## Data Analysis and Visualization

In this script, I've taken a pragmatic approach to handle missing values without extensive data analysis and visualization. Here's why:

- **No Heat Maps**: While heat maps and other visualizations can be poIrful tools to explore relationships betIen columns, I've opted not to use them. This is because I have a basic understanding of the variables in the data and how they are interconnected. Our primary objective is to handle missing values efficiently and not to perform in-depth data analysis or correlation studies.

- **No Univariate Analysis**: I haven't conducted univariate analysis for any variable in this script. Univariate analysis can be valuable for understanding the distribution of individual variables, identifying outliers, and making data-driven decisions. HoIver, our focus here is on addressing missing data, and I're not conducting a comprehensive analysis of the dataset.

I acknowledge that data analysis and visualization can be essential for many data science projects, but in this specific script, I've chosen to emphasize the missing value handling process. Feel free to incorporate visualizations and exploratory analysis in your data projects as per your specific needs and objectives.

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
- Identify missing values in the POSTAL CODE columns.
- Fill missing POSTAL CODE values based on the known city-postal codes using a mapping dictionary.
- Manually fill missing POSTAL CODE values for specific rows.

### Filling Missing CITY Values

- Create a mapping dictionary for postal codes to city names.
- Use the mapping dictionary to fill missing CITY values based on postal codes.

### Filling Missing CAR TYPE Values

- Fill missing CAR TYPE values with the mode (most common value) of the CAR TYPE column.

### Filling Missing TRAVEL TIME Values

- Analyze TRAVEL TIME and fill missing values with the median to handle outliers.

### Filling Missing EDUCATION Values

- Observe that EDUCATION and JOB columns are related.
- Fill missing EDUCATION values based on the JOB column, leveraging the job-specific mode of education to ensure data accuracy.

### Filling Missing SEX Values

- Fill missing SEX values with the mode (most common value) of the SEX column.

### Filling Missing MARITAL STATUS Values

- Observe the MARITAL STATUS column is dependent on SEX or EDUCATION column
- Fill missing MARITAL STATUS values with the mode (most common value) of the MARITAL STATUS column.

### Filling Missing CAR AGE Values

- Fill missing CAR AGE values with the mean (average) of the CAR AGE  column.

### Filling Missing MILES CLOCKED Values

- Observe the MILES CLOCKEDS column is dependent on CAR AGE or CAR TYPE column
- Fill missing  MILES CLOCKED values based on the CAR TYPE column, leveraging the (which are free from outliners)car type with specific mean of miles clocked, & remainning car type with specific median of miles clocked  to ensure data accuracy.

### Filling Missing USE Values

- Observe that USE and JOB columns are related.
- Fill missing USE values based on the JOB column, leveraging the job-specific mode of use to ensure data accuracy.

### Filling Missing INCOME Values

- Observe that  JOB, EDUCATION, and INCOME columns are related
- Fill missing  INCOME values based on the JOB & EDUCATION column, leveraging the (which are free from outliners wrt income)JOB & EDUCATION with specific mean of INOME clocked, & remainning JOB & EDUCATION with specific median of INCOME  to ensure data accuracy.
  
### Filling Missing JOB Values

- Observe that  JOB, EDUCATION, and INCOME columns are related
- Fill missing JOB values based on available data, including JOB, EDUCATION, and INCOME analysis.
- To achieve this:

1. Create a reference table that computes the mean salary for each combination of education levels (rows) and job categories (columns).
2. Identify education categories with outliers wrt the income & jobs in the reference table.
3. Replace salary values with the median for education categories that exhibit outliers, while maintaining the reference table for future reference.

This approach ensures that salary values are imputed based on both education and job categories, improving data accuracy.
- Missing JOB values will be imputed based on a reference table containing mean salaries for distinct education and nearest income combinations.

### Filling Remaining Missing Values

- Complete missing EDUCATION values by referencing the salary-based table.
- Impute the remaining JOB values by considering EDUCATION  as previously described
- Impute the remaining USE values by considering JOB as previously described.
  
## Saving the Cleaned Dataset

The script saves the cleaned dataset to an Excel file named "EDA_Finished_Cars.xlsx" without the index column.

### Three Files:

1. **EDA Cars-1.xlsx**: This is the original dataset with missing values.
2. **EDA_Cars.ipynb**: The Python script where data exploration and missing value handling are performed.
3. **EDA_Finished_Cars.xlsx**: The final cleaned dataset after handling missing values.

## Running the Script

To run the script successfully, ensure you have the required dependencies installed. Place the "EDA Cars-1.xlsx" file in the same directory as the script. After running the script, the cleaned dataset will be saved in the same directory as "EDA_Finished_Cars.xlsx."

Feel free to modify the script or use the principles outlined here for your own data preprocessing tasks.
