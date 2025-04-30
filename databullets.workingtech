# 🧠 DataBullets FY24 Procurement Analysis
# This script provides a basic structure for data analysis and forecasting
# related to centralized procurement for Virginia DPS.

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load procurement data
# Replace 'data/procurement_data.csv' with the actual path to your dataset
try:
    data = pd.read_csv('data/procurement_data.csv')
    print("✅ Data loaded successfully.")
except FileNotFoundError:
    print("⚠️ Data file not found. Please check the file path.")
    data = pd.DataFrame()

# Step 2: Clean and Prepare Data
if not data.empty:
    # Example cleaning: drop missing values
    data.dropna(inplace=True)

    # Optional: convert columns to appropriate types
    if 'Spend' in data.columns:
        data['Spend'] = data['Spend'].astype(float)

# Step 3: Simple Rolling Forecast Example
if not data.empty and 'Date' in data.columns and 'Spend' in data.columns:
    # Convert 'Date' to datetime
    data['Date'] = pd.to_datetime(data['Date'])

    # Sort by date
    data = data.sort_values('Date')

    # Apply rolling average forecast
    data['Forecast'] = data['Spend'].rolling(window=3).mean()

    # Plot actual vs forecast
    plt.figure(figsize=(10, 5))
    plt.plot(data['Date'], data['Spend'], label='Actual Spend')
    plt.plot(data['Date'], data['Forecast'], label='Forecast (3-month MA)', linestyle='--')
    plt.xlabel('Date')
    plt.ylabel('Spend')
    plt.title('Procurement Spend Forecast (FY24)')
    plt.legend()
    plt.grid(True)
    plt.xticks(rotation=45)
    plt.tight_layout()
    plt.show()
else:
    print("⚠️ Data is incomplete or missing required columns.")
