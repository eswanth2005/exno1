<h1 align="center">Ex. 1   Data Cleaning and Outlier Detection & Removal</h1>

### Name: ESWANTH KUMAR K
### Reg No:212223040046
# AIM:
### To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation:
### Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm:
### STEP 1:
#### Read the given Data

### STEP 2:
#### Get the information about the data

### STEP 3:
#### Remove the null values from the data

### STEP 4:
#### Save the Clean data to the file

### STEP 5:
#### Remove outliers using IQR

### STEP 6:
#### Use zscore of to remove outliers

# Coding:

<h3 align="center">Data Cleaning</h3>

```py
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df.head()
```
![image](https://github.com/user-attachments/assets/1b837a70-30a3-4074-a4ff-ce1bbe00fbdf)

```py
df.tail()
```
![image](https://github.com/user-attachments/assets/daf33a76-b826-4c80-a529-ebeea395b3bb)


```py
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/b54d9c51-c6e3-45b9-964e-03b87a44c898)


```py
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/d5fe9bb2-1c5f-4bfd-ad81-b5d0883358f5)

```py
df.dropna()
```
![image](https://github.com/user-attachments/assets/9d62c9f8-4bb9-4d55-be4c-656530138457)

```py
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/0034c3ab-8483-4e33-81dc-1cbc058d4557)

```py
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/f169692f-033b-4220-ab07-af8a7367da26)

```py
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/ebbf8de1-407b-4037-bfb6-5786b8c9c4c5)

```py
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/187dac78-6eb7-4287-acf2-f14083bcd520)

```py
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/22683090-e70a-4f63-b32c-88c67da64c70)


<hr><hr>

<h3 align="center">IQR(Inter Quartile Range)</h3>

```py
import pandas as pd
```
```py
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/47a1a695-ab25-4db0-b22c-129ee7f52966)

```py
ir.describe()
```
![image](https://github.com/user-attachments/assets/c964e725-79bf-46c1-a30e-b9b77c1049e6)

```py
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/f3d775b3-a5d5-4ab1-b7f1-2d8fbfe23428)

```py
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
![image](https://github.com/user-attachments/assets/f04434b1-bf72-4abc-9619-8ca91de57818)

```py

rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/86f73614-e63f-4cf5-98ac-5c83173d0465)

```py
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
![image](https://github.com/user-attachments/assets/c299baa9-1d8e-49cc-b3da-e5a7a785b886)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/bc85434b-efd2-4d29-852b-c7bed61f6271)

<hr><hr>

<h3 align="center">Z-Score</h3>

```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```py
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/b797f4ec-8ec7-4698-9a8f-d9d17f9b632c)

```py
z=np.abs(stats.zscore(dataset['height']))
z
```
![image](https://github.com/user-attachments/assets/e744404a-1350-447d-820f-b30a1c6ba765)

```py
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/63a97873-df4d-41d5-9e2d-384da1699fb9)


## Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
