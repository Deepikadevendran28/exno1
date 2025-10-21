<img width="830" height="576" alt="image" src="https://github.com/user-attachments/assets/67b81c2d-a797-41e0-987b-c7f9be1a8e01" /># Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
import numpy as np
from scipy import stats

# Function to display initial information about the dataset
def initial_data_info(df):
    print("Info:")
    print(df.info())
    print("\nDescribe:")
    print(df.describe())
    print("\nNull values per column:")
    print(df.isnull().sum())
    print('=' * 40)

# Function to remove null values
def remove_nulls(df):
    return df.dropna()

# Function to remove outliers using the IQR method
def remove_outliers_iqr(df, columns):
    for col in columns:
        Q1 = df[col].quantile(0.25)
        Q3 = df[col].quantile(0.75)
        IQR = Q3 - Q1
        lower = Q1 - 1.5 * IQR
        upper = Q3 + 1.5 * IQR
        df = df[(df[col] >= lower) & (df[col] <= upper)]
    return df

# Function to remove outliers using the Z-score method
def remove_outliers_zscore(df, columns, thresh=3):
    for col in columns:
        z = np.abs(stats.zscore(df[col].dropna()))
        filtered_entries = (z < thresh)
        valid_indices = df[col].dropna().index[filtered_entries]
        df = df.loc[valid_indices]
    return df

# List of dataset filenames
file_names = [
    "Data_set.csv",
    "heights.csv",
    "iris.csv",
    "Loan_data.csv",
    "SAMPLEIDS (1).csv"
]

# Process each file one by one
for file in file_names:
    print(f'Processing file: {file}')
    df = pd.read_csv(file)
    
    print("Initial Info")
    initial_data_info(df)
    
    # Remove nulls
    df_no_nulls = remove_nulls(df)
    print("After Removing Nulls:")
    print(df_no_nulls.shape)
    
    # Select numeric columns
    numeric_cols = df_no_nulls.select_dtypes(include=[np.number]).columns.tolist()
    
    # Remove outliers using IQR method
    df_iqr = remove_outliers_iqr(df_no_nulls.copy(), numeric_cols)
    print("After Removing Outliers (IQR method):", df_iqr.shape)
    
    # Remove outliers using Z-score method
    df_z = remove_outliers_zscore(df_no_nulls.copy(), numeric_cols)
    print("After Removing Outliers (Z-score method):", df_z.shape)
    
    print('=' * 80)
```



<img width="470" height="559" alt="Screenshot 2025-10-21 112036" src="https://github.com/user-attachments/assets/634ebc38-5947-49f8-a2af-b7d0e7e65f3c" />
<img width="721" height="594" alt="Screenshot 2025-10-21 112056" src="https://github.com/user-attachments/assets/561bd002-7e24-4528-9fb4-be5dc99e05c1" />
<img width="539" height="598" alt="Screenshot 2025-10-21 112113" src="https://github.com/user-attachments/assets/8ac7353d-dbe9-437f-8fdb-e0659375fc45" />
<img width="578" height="594" alt="Screenshot 2025-10-21 112139" src="https://github.com/user-attachments/assets/8aebecae-f0d6-4409-87c4-44c426d444e4" />
<img width="591" height="587" alt="Screenshot 2025-10-21 112204" src="https://github.com/user-attachments/assets/cb6aac74-0d17-473f-b8f4-56944f4c3bda" />
<img width="625" height="590" alt="Screenshot 2025-10-21 112218" src="https://github.com/user-attachments/assets/1045f662-0fcd-4ab3-b9ca-5c07f1c534d7" />
<img width="627" height="592" alt="Screenshot 2025-10-21 112232" src="https://github.com/user-attachments/assets/ee3e51df-7f03-4b62-8593-96a2852dd9c4" />
<img width="830" height="576" alt="Screenshot 2025-10-21 112243" src="https://github.com/user-attachments/assets/4de7fb7b-6149-4e31-ba7e-ffb53987a3ba" />


# Result
          The code is executed successfully.
