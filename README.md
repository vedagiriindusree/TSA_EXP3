# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
### Date:02/09/2025 

## AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
## ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
## PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

df = pd.read_csv("cardekho.csv")

print(df.columns)
data = df['selling_price'].values  

N = len(data)
lags = range(35)
autocorr_values = []

mean_data = np.mean(data)
variance_data = np.var(data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)  # Normalize by variance

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values, use_line_collection=True)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()

```

## OUTPUT:

<img width="992" height="710" alt="image" src="https://github.com/user-attachments/assets/22716b39-4d06-45c2-beeb-adc1ff700e54" />

## RESULT:

Thus we have successfully implemented the auto correlation function in python.
