# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
# AIM
To detect and remove the outliers in the given data set and save the final data.
# ALGORITHM
Step 1: Import the required packages(pandas,numpy,scipy)

Step 2: Read the given csv file

Step3: Convert the file into a dataframe and get information of the data.

Step 4: Remove the non numerical data columns using drop() method.

Step 5: Detect the outliers in the data set using z scores method.

Step 6: Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7: Check if the outliersare removed from data set using graphical methods.

Step 8: Save the final data set into the file
# CODE
## bhp.csv
```
import numpy as np
import pandas as pd
from scipy import stats
a = pd.read_csv('bhp.csv')
df = pd.DataFrame(a['price_per_sqft'])
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]
print(df1)
z = np.abs(stats.zscore(df))
df1 = df1[(z < 3)]
print(df1)
```
## height_weight.csv
```
import numpy as np
import pandas as pd
from scipy import stats
a = pd.read_csv('height_weight.csv')
df = pd.DataFrame(a['height'])
print(df)
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]
print(df1)
df2 = pd.DataFrame(a['weight'])
print(df2)
q1 = df2.quantile(0.25)
q3 = df2.quantile(0.75)
IQR = q3 - q1
df2_new = df2[((df2 >= q1 - 1.5 * IQR) & (df2 <= q3 + 1.5 * IQR))]
print(df2_new)
```
# OUTPUT
## bhp.csv
![image](https://user-images.githubusercontent.com/119558093/229703367-2cca41f4-6a17-49a3-9aa6-124eea10932d.png)
![image](https://user-images.githubusercontent.com/119558093/229703436-84972743-be2f-43ab-b79a-bb374c7d3b1a.png)
![image](https://user-images.githubusercontent.com/119558093/229703551-73e26b14-bdfb-4fd9-b5c6-b142091e5dad.png)
## height_weight.csv
![image](https://user-images.githubusercontent.com/119558093/229703816-852df5ae-e520-46e6-9f50-850063cfe3b4.png)
![image](https://user-images.githubusercontent.com/119558093/229703883-fbd4a24a-0b4b-4af4-a496-4e3b6ca85fca.png)
![image](https://user-images.githubusercontent.com/119558093/229704000-fb2eb55b-4e0f-4cd3-a11b-3c0b6d414ef9.png)
# RESULT
Thus the required output is displayed.











