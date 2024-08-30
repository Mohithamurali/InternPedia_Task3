import pandas as pd

# File paths to the uploaded CSV files
file_path_1 = '/content/Unemployment_Rate_upto_11_2020.csv'
file_path_2 = '/content/Unemployment in India.csv'

# Load the CSV files into DataFrames
df1 = pd.read_csv(file_path_1)
df2 = pd.read_csv(file_path_2)

# Display the first few rows of each dataset
print("Dataset 1 Head (Unemployment Rate up to 11_2020):")
print(df1.head())

print("\nDataset 2 Head (Unemployment in India):")
print(df2.head())
# Check if necessary columns exist in Dataset 1
if 'Unemployed_Persons' in df1.columns and 'Labor_Force' in df1.columns:
    # Calculate the Unemployment Rate
    df1['Unemployment_Rate'] = (df1['Unemployed_Persons'] / df1['Labor_Force']) * 100

    # Display the DataFrame with the calculated Unemployment Rate
    print("\nCalculated Unemployment Rates for Dataset 1:")
    print(df1[['Year', 'Month', 'Unemployment_Rate']].head())

# Example: Plotting the Unemployment Rate over time for Dataset 1
import matplotlib.pyplot as plt

if 'Year' in df1.columns and 'Month' in df1.columns and 'Unemployment_Rate' in df1.columns:
    plt.figure(figsize=(10, 6))
    plt.plot(df1['Year'].astype(str) + '-' + df1['Month'], df1['Unemployment_Rate'], marker='o', linestyle='--')
    plt.title('Unemployment Rate Over Time (Dataset 1)')
    plt.xlabel('Time')
    plt.ylabel('Unemployment Rate (%)')
    plt.xticks(rotation=45)
    plt.grid(True)
    plt.show()
    # Display summary statistics for Dataset 2
print("\nSummary Statistics for Dataset 2:")
print(df2.describe())

# Example: Plotting any relevant data from Dataset 2
if 'Date' in df2.columns and 'Unemployment Rate' in df2.columns:
    plt.figure(figsize=(10, 6))
    plt.plot(pd.to_datetime(df2['Date']), df2['Unemployment Rate'], marker='o', linestyle='--', color='r')
    plt.title('Unemployment Rate Over Time (Dataset 2)')
    plt.xlabel('Date')
    plt.ylabel('Unemployment Rate (%)')
    plt.grid(True)
    plt.show()
