# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 27/02/2024

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
#### Import the necessary Packages
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```
#### Load the dataset
```
data=pd.read_csv('/content/international-airline-passengers.csv')
```
#### PLot the data without Conversion
```
x=data['Month']
y=data['International airline passengers: monthly totals in thousands. Jan 49 ? Dec 60']
plt.xlabel('Month')
plt.ylabel('International airline passengers: monthly totals in thousands.')
plt.plot(x,y)
```
#### REGULAR DIFFERENCING
```
data3=data
data3['diff']=data3['International airline passengers: monthly totals in thousands. Jan 49 ? Dec 60'].diff(periods=1)
data3=data3.dropna()
x=data3['Month']
y=data3['diff']
plt.xlabel('Month')
plt.ylabel('International airline passengers: monthly totals in thousands.')
plt.plot(x,y)
```
#### SEASONAL ADJUSTMENT
```
data1=data
data1['SeasonalAdjustment'] = data1['International airline passengers: monthly totals in thousands. Jan 49 ? Dec 60'] - data1['International airline passengers: monthly totals in thousands. Jan 49 ? Dec 60'].shift(12)
data1['SeasonalAdjustment'].dropna()
x=data1['Month']
y=data1["SeasonalAdjustment"]
plt.xlabel('Month')
plt.ylabel('International airline passengers: monthly totals in thousands.')
plt.plot(x,y)
```
#### LOG TRANSFORMATION
```
data2=data
data2['log']=np.log(data2['diff']).dropna()
data2=data2.dropna()
x=data2['Month']
y=data2['log']
plt.xlabel('Month')
plt.ylabel('International airline passengers: monthly totals in thousands.')
# plt.figure(figsize=(8, 6)) 
plt.plot(x,y)
```

### OUTPUT:
#### WITHOUT CONVERSION:
![image](https://github.com/manojvenaram/TSA_EXP1B/assets/94165064/e53c563f-adcf-4c9b-ace6-c3e228db664b)


#### REGULAR DIFFERENCING:
![image](https://github.com/manojvenaram/TSA_EXP1B/assets/94165064/817714f5-36e2-4a03-9f80-6f1a51e29ec4)


#### SEASONAL ADJUSTMENT:
![image](https://github.com/manojvenaram/TSA_EXP1B/assets/94165064/a3fddba6-27a3-47e9-bb54-5a92303cee66)



#### LOG TRANSFORMATION:
![image](https://github.com/manojvenaram/TSA_EXP1B/assets/94165064/47b91df2-4a57-4312-bc53-efd42b674a08)



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
