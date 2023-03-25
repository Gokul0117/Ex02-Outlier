# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

# AIM:

TO detect and remove the outliers in the given data set and save the final data.

# Algorithm:

## Step 1

Import the required packages(pandas,numpy,scipy)

## Step 2

Read the given csv file

## Step 3

Convert the file into a dataframe and get information of the data.

## Step 4

Remove the non numerical data columns using drop() method.

## Step 5

Detect the outliers in the data set using z scores method.

## Step 6

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

## Step 7

Check if the outliersare removed from data set using graphical methods.

## Step 8

Save the final data set into the file.

# Program:

## (1) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe

```py
import pandas as pd
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
sns.boxplot(data=df)
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.35)
q3 = df['price_per_sqft'].quantile(0.65)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
high = q3+1.5*IQR
low = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]
df1
sns.boxplot(x="price_per_sqft",data=df1)
df1.shape
```

## (1) & (2) Examine price_per_sqft column and use zscore of 3 to remove outliers.

```py
from scipy import stats
import numpy as np
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
df2.shape
sns.boxplot(x="price_per_sqft",data=df2)
```

## (4) (i)For the data set height_weight.csv detect weight outliers using IQR method

```py
df3 = pd.read_csv("/content/height_weight.csv")
df3
sns.boxplot(x="weight",data=df3)
q1 = df3["weight"].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df4 =df3[((df3['weight']>=low)&(df3['weight']<=high))]
df4
df4.shape
sns.boxplot(x="weight",data=df4)
```

## (4)(ii) For the data set height_weight.csv detect height outliers using IQR method.

```py
sns.boxplot(x="height",data=df3)
q1 = df3["height"].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df5 =df3[((df3['height']>=low)&(df3['height']<=high))]
df5
df5.shape
sns.boxplot(x="height",data=df5)
```

# OUTPUT:

# DATASET FOR bhp.csv

![output](/1.png)

# bhp Boxplot

![output](/2.png)

# DATASET BOXPLOT WITH OUTLIERS(BHP)

![output](/3.png)

# DATASET WITHOUT OUTLIERS(BHP)

![output](/4.png)

![output](/5.png)

# DATASET BOXPLOT WITHOUT OUTLIERS(BHP)

![output](/6.png)

# Shape

![output](/7.png)

# DATASET AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)

![output](/8.png)

# Shape

![output](/9.png)

# DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)

![output](/10.png)

# DATASET FOR WEIGHT_HEIGHT_CSV

![output](/11.png)

# DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT)

![output](/12.png)

# DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)

![output](/13.png)

![output](/14.png)

# SHAPE

![output](/15.png)

# DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)

![output](/16.png)

# FOR HEIGHT COLUMN WITH OUTLIERS

![output](/17.png)

![output](/18.png)

![output](/19.png)

# Shape

![output](/20.png)

# AFTER REMOVING OUTLIERS BOXPLOT FOR HEIGHT

![output](/21.png)

# Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
