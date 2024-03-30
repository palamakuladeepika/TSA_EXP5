# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
Developed By: Palamakula Deepika
Reg. No: 212221240035
```
```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the Passenger Details
# Replace 'AirPassengers.csv' with the path to your data file
data = pd.read_csv('AirPassengers.csv')

# Ensure that the 'Month' column is in datetime format
data['Month'] = pd.to_datetime(data['Month'])
data['Year'] = data['Month'].dt.year
# Set the 'Month' column as the index
data.set_index('Month', inplace=True)
data.head()

# Plotting the Data
ar1 = data['Year'].values.reshape(-1, 1)
ma1 = data['#Passengers'].values.reshape(-1, 1)
plt.plot(ar1,ma1,label='Data')
plt.title('Plotting the Data')
plt.legend()
plt.show()

# Perform time series decomposition
period=13
result = seasonal_decompose(data,model='multiplicative', period=period)

# Plot the seasonal component
plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

# Plot the trend component
plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

# Plot the original time series
plt.figure(figsize=(12, 6))
plt.subplot(4, 1, 1)
plt.plot(data['#Passengers'], label='original')
plt.title('Original Time Series')
plt.legend()
plt.show()
```
### OUTPUT:

#### FIRST FIVE ROWS:

![image](https://github.com/Pavan-Gv/TSA_EXP5/assets/94827772/13f2fe6f-95f1-4c4b-a325-7beafe29b3fb)


#### PLOTTING THE DATA:

![image](https://github.com/Pavan-Gv/TSA_EXP5/assets/94827772/6dcc5811-918e-46ab-9a98-8d28cb75ec2a)


#### SEASONAL PLOT REPRESENTATION :

![image](https://github.com/Pavan-Gv/TSA_EXP5/assets/94827772/c4786cc7-0cc2-4b88-9c9b-cf346ce2fffe)


#### TREND PLOT REPRESENTATION :


![image](https://github.com/Pavan-Gv/TSA_EXP5/assets/94827772/b4c473b6-096f-4a33-ade3-c8c7de0fa067)


#### OVERAL REPRESENTATION:

![image](https://github.com/Pavan-Gv/TSA_EXP5/assets/94827772/5ca05ec8-262d-4ee4-804e-7297e86747ab)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
