# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# Aim:
TO detect and remove the outliers in the given data set and save the final data.

# Algorithm:
# Step 1
Import the required packages(pandas,numpy,scipy)

# Step 2
Read the given csv file

# Step 3
Convert the file into a dataframe and get information of the data.

# Step 4
Remove the non numerical data columns using drop() method.

# Step 5
Detect the outliers in the data set using z scores method.

# Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

# Step 7
Check if the outliersare removed from data set using graphical methods.

# Step 8
Save the final data set into the file.

# Program:
# (1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe

DEVELOPED BY: YOGABHARATHI S
REGISTER NO:212222230179
```
import pandas as pd
import numpy as np
import seaborn as sns

df = pd.read_csv("/content/bhp.csv")
df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_per_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
```
# (3)Examine price_per_sqft column and use zscore of 3 to remove outliers
```
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2

print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
```
# (4)(i) For the data set height_weight.csv detect weight outliers using IQR method
```
df3 = pd.read_csv("height_weight.csv")
df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape

sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))]
df4

df4.shape

sns.boxplot(x="weight",data=df4)
```
# (4)(ii) For the data set height_weight.csv detect height outliers using IQR method
```
sns.boxplot(x="height",data=df3)
q1 = df3['height'].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))]
df5

df5.shape

sns.boxplot(x="height",data=df5)
```
# OUTPUT:
# (1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
# Dataset:
![Screenshot 2023-08-30 221632](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/76c7b641-8530-4b3c-bc8f-f87b537e9c23)

# Dataset Head:
![Screenshot 2023-08-30 221641](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/a4e07716-49c0-4cb9-8327-bc1a228089c8)

# Dataset Info:
![Screenshot 2023-08-30 221656](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/2bd7ae67-aa9d-469a-a66d-94ab6699d798)

# Dataset Describe:
![Screenshot 2023-08-30 221649](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/61091282-24bb-48eb-a8e6-6682bdfb80c5)

# Null Values:
![Screenshot 2023-08-30 221738](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/25a39f68-6992-43f7-b7fd-415d640ce518)

# Dataset Shape:
![Screenshot 2023-08-30 221705](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/b778cf49-071c-4c49-8c35-3ea455601305)

# Box plot of price_per_sqft column with outliers:
![Screenshot 2023-08-30 221749](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/b643622d-1790-424b-b514-fd85c18c3676)

# price_per_sqft - Dataset after removing outliers:
![Screenshot 2023-08-30 221757](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/2355e7d6-b883-49a5-a268-6e0060ff9df7)
![Screenshot 2023-08-30 221805](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/4d6473d8-d0f3-43fa-80a7-ac2fe4fea5d3)

# price_per_sqft - Shape of Dataset after removing outliers:
![Screenshot 2023-08-30 221810](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/d64afa36-0c83-418a-a503-876dca696804)

# Box Plot of price_per_sqft column without outliers:
![Screenshot 2023-08-30 221817](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/ace5a55e-6902-43aa-b90c-032ec7d20533)

# (3) Examine price_per_sqft column and use zscore of 3 to remove outliers
# Dataset after removal of outlier using z score:
![Screenshot 2023-08-30 221825](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/95b01d67-a980-42c1-af79-1606898eb60a)

# Shape of Dataset after removal of outlier using z score:
![Screenshot 2023-08-30 221918](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/fdb78f4d-71f6-4ecd-b24d-4b4bf788b386)

# (4) For the data set height_weight.csv detect weight and height outliers using IQR method:
# Dataset:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/c5edf9ef-748e-40a2-b8b5-9a98f8ee35a5)
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/175d5808-7146-4643-9821-bee466860067)

# Dataset Head:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/1102e08d-e2bd-43b0-b233-3ac814479838)

![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/45ab2b2c-2c05-433e-b55c-56caebc61d4d)

# Dataset Info:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/814478d5-1cb1-4534-a6d6-5be8da7abf18)
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/4980b389-c33c-432e-996a-f1f2fe23ad15)

# Dataset Describe:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/1318f1ba-a052-48bd-8453-03ac28b275b5)
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/55bde9cd-00e2-4323-b449-3f942ad8da84)

# Null Values:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/8e7d37d7-dfa6-4fa7-b19f-1438a402de3f)

![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/75d702bc-18fa-42a8-8959-dcad0e6b5e18)

# Dataset Shape:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/574ce2cb-a759-47ee-83b1-b37e85b2040a)

![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/12dc8ee4-125b-4c53-a348-2ab0f968e642)

# Weight - With outliers:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/7f298cea-7402-4126-81e0-71de9ef6a18d)

# Weight - Dataset after removing Outliers using IQR method:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/5d0151c7-158b-4a3b-9ec1-1f62c728f382)

# Weight - Shape of Dataset after removing Outliers using IQR method:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/a7163d89-d801-497c-83af-8bc418191e20)

# Weight - Without Outliers using IQR method:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/a8dd2d81-16b2-4b0c-88f4-059f6a45b270)

# Height - With outliers:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/aeb6a637-65ba-4e32-83df-e0ce22ba7ebc)

![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/b4b35c6f-be69-4282-be10-59b8178b09e2)

# Height - Dataset after removing Outliers using IQR method:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/b0658206-51fb-4acd-8c3b-43488c86b5bb)

![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/2c2ac983-3303-4614-8d8a-c35a6726ffb8)

# Height - Shape of Dataset after removing Outliers using IQR method:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/5f46fbe5-8439-4e86-bcd9-0fbd4ff96405)

![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/34ef27a8-7657-4099-9040-0cd718f31d2f)

# Height - Without Outliers using IQR method:
![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/d1ff62f4-6f56-4041-9510-bfbb11300c33)

![image](https://github.com/Yogabharathi3/ODD2023---Datascience---Ex-02/assets/118899387/14b9077a-e937-4301-9010-dfc58d33bd75)

# Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
