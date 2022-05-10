# Ex-03EDA

## AIM
To perform EDA on the given data set. 

# Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and 
anomalies to direct specific testing of your hypothesis.
 

# ALGORITHM
### STEP 1
import packages that are required for data cleaning,removing outliears and exploatory data analysis.
### STEP 2
Replace the null value using anyone of the method.
### STEP 3
to analyse the given dataset using boxplot method.
### STEP 4
using inter quantile range method to remove the outliear.
### STEP 5
to analyse the graphical method for categorical data use countplot method.
### STEP 6
to represent the univariate distribution of a data use displot method.
### STEP 7
the relationship between multiple variables is quantitatively analysed using cross tabulation method.
### STEP 8:
to represent the relationships between two variables, one plotted on each axis using heatmap method.
# CODE:
```
import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("titanic_dataset.csv")
df.info()
df.isnull().sum()
df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df["Cabin"]=df["Cabin"].fillna(df["Cabin"].mode()[0])
df.info()
df.isnull().sum()
df.boxplot()
cols = ['Age', 'SibSp','Parch','Fare'] # one or more.
Q1 = df[cols]. quantile(0.25)
Q3 = df[cols]. quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))). any(axis=1)]
df.boxplot()
df.info()
df["Embarked"].value_counts()
df["Pclass"].value_counts()
df["Survived"].value_counts()
sns.countplot(x="Survived",data=df)
sns.countplot(x="Pclass",data=df)
sns.countplot(x="Sex",data=df)
sns.displot(df["Fare"])
sns.countplot(x="Pclass",hue="Survived",data=df)
sns.countplot(x="Sex",hue="Survived",data=df)
sns.displot(df[df["Survived"]==0]["Age"])
sns.displot(df[df["Survived"]==1]["Age"])
pd.crosstab(df["Pclass"],df["Survived"])
pd.crosstab(df["Sex"],df["Survived"])
df.corr()
sns.heatmap(df.corr(),annot=True)
```
# OUTPUT:
### DATA CLEANING:
![output1](https://user-images.githubusercontent.com/94168395/167650037-e809fcbc-3528-4ac5-8766-3c5570a1eac4.png)
![output2](https://user-images.githubusercontent.com/94168395/167650210-cb3a4d0c-8226-4806-9f75-1f51dbe1b61a.png)
### IMPLEMENTATION OF METHODS:
![2](https://user-images.githubusercontent.com/94168395/167650839-0fd4ae07-1730-41e3-afe9-166c6c341646.jpg)
![3](https://user-images.githubusercontent.com/94168395/167650896-c1e79490-35f1-4e24-b882-2dce8eed1076.jpg)
### REMOVING OUTLIERS:
![output4](https://user-images.githubusercontent.com/94168395/167650991-10cb28fa-9d98-4569-8a1c-ab9daceb2eeb.png)
![4](https://user-images.githubusercontent.com/94168395/167651167-f1af6c9d-16b2-4610-b83a-0e8bc1f69961.jpg)
![6](https://user-images.githubusercontent.com/94168395/167651328-e5425358-d505-4e92-9408-d2ad59323518.jpg)
![7](https://user-images.githubusercontent.com/94168395/167651431-eb43dffc-3934-4abe-b7bc-f350f1a7b2fd.jpg)
### DATA ANALYSIS:
![output9](https://user-images.githubusercontent.com/94168395/167651689-8e4e944a-d324-419b-b5dc-c239c116ac9c.png)
![output12](https://user-images.githubusercontent.com/94168395/167651767-306d1646-b1cf-4c93-aeb9-eb68c6de36af.png)
![output13](https://user-images.githubusercontent.com/94168395/167651820-5a08d8e6-38c1-49dd-8864-7a8ca1dd81e2.png)

![output10](https://user-images.githubusercontent.com/94168395/167651877-6ce9ef3f-4fe5-41eb-9eec-595b1e1ee5e7.png)
![output11](https://user-images.githubusercontent.com/94168395/167651956-61647806-8eea-4825-bcfd-d5009662a83e.png)

### CORRELATION METHOD:
![16](https://user-images.githubusercontent.com/94168395/167652162-85749a2a-d57d-48d0-a027-97745f6661cf.jpg)

# OUTPUT:
Thus the data of the dataset is analyzed using Exploratory data analysis









