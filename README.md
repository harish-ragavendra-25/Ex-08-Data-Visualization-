# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
DEVELOPED BY: HARISH RAGAVENDRA S
REGISTER NO: 212222230045
```
```
import pandas as pd
df=pd.read_csv('/Superstore.csv',encoding='windows-1252')
df
```
```
df.isnull().sum()
```
```
import pandas as pd
import matplotlib.pyplot as plt
df.drop('Row ID',axis=1,inplace=True)
df.drop('Order ID',axis=1,inplace=True)
df.drop('Customer ID',axis=1,inplace=True)
df.drop('Customer Name',axis=1,inplace=True)
df.drop('Country',axis=1,inplace=True)
df.drop('Postal Code',axis=1,inplace=True)
df.drop('Product ID',axis=1,inplace=True)
df.drop('Product Name',axis=1,inplace=True)
df.drop('Order Date',axis=1,inplace=True)
df.drop('Ship Date',axis=1,inplace=True)
print("Updated dataset")
df
```
```
plt.figure(figsize=(12,10))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
```
cols=['Sales','Quantity','Discount','Profit']
q1=df[cols].quantile(0.75)
q3=df[cols].quantile(0.25)
iqr=q3-q1
low=q1+1.5*iqr
high=q3-1.5*iqr
df2=df[(df[cols]>low)&(df[cols]<high)]
plt.title("Data after removing outlier")
df2.boxplot()
plt.show()
```
```
import pandas as pd
import matplotlib.pyplot as plt
df2.drop(['Region','State','City','Segment','Ship Mode','Category','Sub-Category'],axis=1,inplace=True)
print("Updated dataset")
df2
```
```
#data visualization
#line plots
import seaborn as sns
sns.lineplot(x="Sub-Category",y="Sales",data=df,marker='o')
plt.title("Sub Categories vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.lineplot(x="Category",y="Profit",data=df,marker='o')
plt.xticks(rotation = 90)
plt.title("Categories vs Profit")
plt.show()

sns.lineplot(x="Region",y="Sales",data=df,marker='o')
plt.xticks(rotation = 90)
plt.title("Region area vs Sales")
plt.show()

sns.lineplot(x="Category",y="Discount",data=df,marker='o')
plt.title("Categories vs Discount")
plt.show()

sns.lineplot(x="Sub-Category",y="Quantity",data=df,marker='o')
plt.xticks(rotation = 90)
plt.title("Sub Categories vs Quantity")
plt.show()
```
```
#count plot
plt.figure(figsize=(10,7))
sns.countplot(x ='Segment', data = df,hue = 'Sub-Category')
sns.countplot(x ='Region', data = df,hue = 'Segment')
sns.countplot(x ='Category', data = df,hue='Discount')
sns.countplot(x ='Ship Mode', data = df,hue = 'Quantity')
```
```
#Histogram
sns.histplot(data = df,x = 'Region',hue='Ship Mode')
sns.histplot(data = df,x = 'Category',hue='Quantity')
sns.histplot(data = df,x = 'Sub-Category',hue='Category')
plt.xticks(rotation = 90)
plt.show()
sns.histplot(data = df,x = 'Quantity',hue='Segment')
plt.hist(data = df,x = 'Profit')
plt.show()
```
```
#bar plots
sns.barplot(x="Sub-Category",y="Sales",data=df)
plt.title("Sub Categories vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Category",y="Profit",data=df)
plt.title("Categories vs Profit")
plt.show()

sns.barplot(x="Sub-Category",y="Quantity",data=df)
plt.title("Sub Categories vs Quantity")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Category",y="Discount",data=df)
plt.title("Categories vs Discount")
plt.show()

plt.figure(figsize=(12,7))
sns.barplot(x="State",y="Sales",data=df)
plt.title("States vs Sales")
plt.xticks(rotation = 90)
plt.show()

plt.figure(figsize=(25,8))
sns.barplot(x="State",y="Sales",hue="Region",data=df)
plt.title("State vs Sales based on Region")
plt.xticks(rotation = 90)
plt.show()
```
```
#KDE plot
sns.kdeplot(x="Profit", data = df,hue='Category')
sns.kdeplot(x="Sales", data = df,hue='Region')
sns.kdeplot(x="Quantity", data = df,hue='Segment')
sns.kdeplot(x="Discount", data = df,hue='Segment')
```
```
#violin plot
sns.violinplot(x="Profit",data=df)
sns.violinplot(x="Discount",y="Ship Mode",data=df)
sns.violinplot(x="Quantity",y="Ship Mode",data=df)
```
# OUPUT
![Screenshot from 2023-05-30 18-19-53](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/7c1d5ff6-54d5-4146-9dca-d8ee7113f24a)
![Screenshot from 2023-05-30 18-19-49](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/18b2e73c-feb5-4030-a2ef-aba799c43250)
![Screenshot from 2023-05-30 18-19-45](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/92e50b9e-595b-4066-9f5e-6e12f04f46de)
![Screenshot from 2023-05-30 18-19-41](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/32f0966b-b04f-46d4-9bff-87a0e93794e4)
![Screenshot from 2023-05-30 18-19-37](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/9aa3240c-78f5-45d1-959a-0a61709f5658)
![Screenshot from 2023-05-30 18-19-34](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/1779c795-864a-490b-8927-c1e72f43ca21)
![Screenshot from 2023-05-30 18-19-30](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/43eb2192-a726-4a87-aa31-aa198360f0ba)
![Screenshot from 2023-05-30 18-19-27](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/5811e3b7-c4ae-499d-969f-ef280d0574c6)
![Screenshot from 2023-05-30 18-19-23](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/c45b15dc-c5b9-4dfe-9e2a-ad44726cb4ff)
![Screenshot from 2023-05-30 18-19-21](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/99ffd138-e5e9-4206-8cca-f2d39c22fb0d)
![Screenshot from 2023-05-30 18-19-09](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/1a1b85b2-f30e-48ba-b789-50892453026e)
![Screenshot from 2023-05-30 18-19-04](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/0a42679d-693a-4dcb-9781-f7de990d0ab3)
![Screenshot from 2023-05-30 18-18-54](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/e43a2324-0c35-4935-a199-5943343f6d12)
![Screenshot from 2023-05-30 18-18-46](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/83fa9244-3852-42e9-9c65-55a2e6ea85df)
![Screenshot from 2023-05-30 18-18-41](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/60345065-f734-4d28-9de9-47d6b9064b72)
![Screenshot from 2023-05-30 18-18-39](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/86b42d24-f7f1-4fc7-be1b-7dd2c7410731)
![Screenshot from 2023-05-30 18-18-36](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/db04b8b1-6e66-4aad-8021-0f00ee0873f8)
![Screenshot from 2023-05-30 18-18-27](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/00b9ac7a-db96-4946-93cc-2a54aac50bd7)
![Screenshot from 2023-05-30 18-18-16](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/c042a3e9-5749-4bce-9ca1-1f9226030a29)
![Screenshot from 2023-05-30 18-18-11](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/4683b59a-f2fd-4648-882d-c4ba9ac2e483)
![Screenshot from 2023-05-30 18-18-07](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/fc9617a7-392c-4e68-9d62-6f33c61b96c0)
![Screenshot from 2023-05-30 18-18-02](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/9dec0c81-12e4-4138-8bf0-a39345b11c25)
![Screenshot from 2023-05-30 18-17-56](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/fca86f38-be06-44dd-8a1c-87010b094834)
![Screenshot from 2023-05-30 18-17-50](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/b16d7c28-49d6-42b5-8bad-bf3d94b314bd)
![Screenshot from 2023-05-30 18-17-45](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/985dff87-4595-43c0-8ef5-ee2b6bc5986b)
![Screenshot from 2023-05-30 18-17-15](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/2924d884-6642-4d4d-af5c-906ac5d98002)
![Screenshot from 2023-05-30 18-16-53](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/82a5adee-c627-4ba2-876a-b1c2421e45e4)
![Screenshot from 2023-05-30 18-16-38](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/18b98ff2-f2de-4f3b-afd5-c07ebf5fc3e0)

# RESULT:
thus the experiment executed sucessfully
