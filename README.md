# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
# ALGORITHM:
STEP 1:
Read the given Data.

STEP 2:
Get the information about the data.

nSTEP 3:
Detect the Outliers using IQR method and Z score.

STEP 4:
Remove the outliers:

STEP 5:
Plot the datas using box plot.

# Program:
```py
DEVELOPED BY: Kanishka.V.S
REGISTER NUMBER: 212222230061

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### Removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)
#New dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### Removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
# Output:
df.head():
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/9b5b50ff-8deb-4dac-841a-74b72b7d8dda)
df.describe():
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/49521d72-c812-4e16-a27d-9e1d0c7daf03)
df.info():
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/480b8300-09f2-49f8-9d8b-5d0f856ff905)
df.shape():
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/5ddaafc1-9040-4942-8dea-b2330845293d)
BOXPLOT BEFORE REMOVING OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/bf049dc9-db0c-4b51-9254-b1dfdc42c8c6)
NEWDATA USING IQR:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/435821f5-5b62-44f4-a3c2-11cbcf704fd1)
OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/6c3bd3e1-1680-4550-acc2-6e2a6c4e2d8d)
newdata.shape:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/b0ee0b40-9bd9-4972-be6b-25c186db57bc)
BOXPLOT AFTER REMOVING OUTLIERS USING IQR:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/2af5a2be-ead5-4176-9def-81d2e014fb8c)
Zscore of 3: NEWDATA USING Zscore:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/d076a1ac-a16b-4b39-8db5-d0f8d4e8fe2f)
OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/47a6b524-4d54-4ece-b263-1e0a18cd4285)
newdata2.shape:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/e47dbc43-e392-469c-be4e-448ea6ff119b)
BOXPLOT AFTER REMOVING OUTLIERS USING Zscore:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/1baacd76-2205-4479-8107-5445f06c1abf)
height_weight.csv:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/1250a9fd-8608-45cb-a4ba-82f9f75f76e4)
dataset.describe():
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/3a9d579e-cea0-4c3d-a704-99bd3e3d82f4)
dataset.info():
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/3242c6d6-81b4-4d46-8bc8-2ff81c5795f0)
BOXPLOT BEFORE REMOVING OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/351f9750-8233-44a8-bd6d-8af3bd6185ff)
HEIGHT OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/45a5cbac-a044-4fd3-bcb8-0b784b324e25)
DATASET AFTER REMOVING HEIGHT OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/fbd164b7-faa4-4009-b98e-44b153f5e410)
BOXPLOT AFTER REMOVING HEIGHT OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/59fdc2f5-fa4b-4bc2-9091-ac88fa710148)
WEIGHT OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/2ac94005-f8f0-4245-9f32-77a18bcad4b9)
DATASET AFTER REMOVING WEIGHT OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/72bba149-cc08-44b6-ba18-eeb047e6c924)
BOXPLOT AFTER REMOVING WEIGHT OUTLIERS:
![image](https://github.com/kanishka2305/ODD2023---Datascience---Ex-02/assets/113497357/7a4f5314-ebe3-4975-a043-6285b3187f90)

# Result:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
