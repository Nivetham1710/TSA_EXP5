# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### AIM:
To illustrate how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and Numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

df = pd.read_csv('US_City_Temp_Data.csv')

df.isnull().sum()

df['time'] = pd.to_datetime(df['time'])

temperature_data = df['new_york']

new_index = pd.date_range(start=temperature_data.index.min(), periods=len(temperature_data), freq='MS')[:len(temperature_data)]

temperature_data.index = new_index

decomposition = seasonal_decompose(temperature_data, model='additive')

# Extract trend, seasonal, and residuals components
trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

# Original data
plt.figure(figsize=(12, 6))
plt.plot(temperature_data, label='Original Temperature')
plt.legend()

# Trend plot
plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend')
plt.legend()

# Seasonal plot (optional)
plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal')
plt.legend()

# Residuals plot (optional)
plt.figure(figsize=(12, 6))
plt.plot(residuals, label='Residuals')
plt.legend()
```

### OUTPUT:
#### FIRST FIVE ROWS:
![image](https://github.com/Nivetham1710/TSA_EXP5/assets/94155183/ad0e604f-4295-4a97-9ca8-284ec4953a77)

#### PLOTTING THE DATA:
![image](https://github.com/Nivetham1710/TSA_EXP5/assets/94155183/4837e797-d63f-4a6a-9262-e9440c4fcfd7)

#### SEASONAL PLOT REPRESENTATION :
![image](https://github.com/Nivetham1710/TSA_EXP5/assets/94155183/a25f088a-2aee-445c-8325-94897339a05e)

#### TREND PLOT REPRESENTATION :
![image](https://github.com/Nivetham1710/TSA_EXP5/assets/94155183/ebac7da6-b21b-4946-a82e-5b3fbf8792d1)

#### RESIDUAL PLOT REPRESENTATION :
![image](https://github.com/Nivetham1710/TSA_EXP5/assets/94155183/fd392f25-a42f-4dd0-9b26-ceb6782aa65c)


### RESULT:
Thus we have created the Python code for the time series analysis and decomposition.
