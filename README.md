# Exno:1
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
from IPython.display import display
from google.colab import files

uploaded = files.upload()

for fn in uploaded.keys():
  print('User uploaded file "{name}" with length {length} bytes'.format(
      name=fn, length=len(uploaded[fn])))

def load_csv(path='Data_set.csv', **read_csv_kwargs):
    """Load CSV and return DataFrame."""
    df = pd.read_csv(path, **read_csv_kwargs)
    print(f"Loaded '{path}' — shape: {df.shape}")
    return df

def basic_eda(df, n=5, describe=True):
    """Display basic info & quick analysis for DataFrame `df`."""
    print("HEAD:")
    display(df.head(n))

    print("TAIL:")
    display(df.tail(n))

    print("SHAPE:", df.shape)

    print("\nDTYPES:")
    print(df.dtypes)

    print("\nINFO:")
    df.info()

    print("\nMISSING VALUES (per column):")
    display(df.isnull().sum())

    if describe:
        print("\nDESCRIBE (all columns):")
        display(df.describe(include='all').transpose())

    print("\nNUMERIC CORRELATION (pearson):")
    display(df.select_dtypes(include=['number']).corr())

    print("\nTOP VALUES FOR NON-NUMERIC COLUMNS:")
    for col in df.select_dtypes(exclude=['number']).columns:
        print(f"  {col}:")
        display(df[col].value_counts(dropna=False).head(10))
       # Call load_csv to create the df variable
      df = load_csv(path='Data_set (2).csv'
      basic_eda(df, n=5)

<img width="1366" height="768" alt="Screenshot 2025-10-17 112802" src="https://github.com/user-attachments/assets/7f329930-f14b-4818-83ac-914a4c0093de" />
<img width="1366" height="768" alt="Screenshot 2025-10-17 112811" src="https://github.com/user-attachments/assets/e56f730f-a4cf-4b7a-a752-cbf85fe37282" />
<img width="1366" height="768" alt="Screenshot 2025-10-17 112818" src="https://github.com/user-attachments/assets/4285a2f7-8094-4f0c-8fbc-0504470f2cde" />
<img width="1366" height="768" alt="Screenshot 2025-10-17 112822" src="https://github.com/user-attachments/assets/610bc96c-9a36-4f48-b6d2-eb745d9a73ff" />






<img width="1366" height="768" alt="Screenshot 2025-10-17 113037" src="https://github.com/user-attachments/assets/6d6b9ea5-7aea-40ac-86e6-e8c1ff3d5019" />

<img width="1366" height="768" alt="Screenshot 2025-10-17 113042" src="https://github.com/user-attachments/assets/e7683b66-29f7-4f5a-b889-57816d20f0f1" />

<img width="1366" height="768" alt="Screenshot 2025-10-17 113047" src="https://github.com/user-attachments/assets/a706bd66-e690-4015-a688-975706155b01" />

<img width="1366" height="768" alt="Screenshot 2025-10-17 113054" src="https://github.com/user-attachments/assets/be7c8259-b0d7-48ee-97cf-d3e64e8f7349" />

```

# Result
          The code is executed successfully.
