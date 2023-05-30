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
# OUPUT:
![Screenshot from 2023-05-30 18-27-08](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/c855b083-5bbc-4dd0-9b6a-2ca774621503)
![Screenshot from 2023-05-30 18-27-01](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/fea41358-04f9-4459-a562-350b02d3f0bd)
![Screenshot from 2023-05-30 18-17-15](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/388874fa-f196-4bea-be45-11cc0f29de2c)
![Screenshot from 2023-05-30 18-17-45](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/4e08bc09-2053-41d9-b863-9a1cb7aad65c)
![Screenshot from 2023-05-30 18-17-50](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/3b811192-6ac0-4ae0-a4a1-c981dd55b3c1)
![Screenshot from 2023-05-30 18-17-56](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/c77b010a-370e-4334-82f6-7546d838136e)
![Screenshot from 2023-05-30 18-18-02](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/973db450-b7b1-4669-8a24-df2ae9ab5fd8)
![Screenshot from 2023-05-30 18-18-07](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/1f607cf3-8659-4c39-bd8b-0a97960b36d2)
![Screenshot from 2023-05-30 18-18-11](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/3d77f902-2ceb-4df4-9732-34d1136925a5)
![Screenshot from 2023-05-30 18-18-16](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/7896d34e-137f-4fdd-b5c9-51d5e8f0cfde)
![Screenshot from 2023-05-30 18-18-27](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/74618c5e-6d28-47dd-bb27-4b054fd35a70)
![Screenshot from 2023-05-30 18-18-36](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/f95b9e2a-9484-46e7-bb8c-9c51f3efa566)
![Screenshot from 2023-05-30 18-18-39](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/85e671ba-3810-4c49-8e0c-e6673a0a59ce)
![Screenshot from 2023-05-30 18-18-41](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/8e2a20c4-5b5b-443d-b334-a95e81a7e69b)
![Screenshot from 2023-05-30 18-18-46](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/981ff710-3bab-4eee-bf76-7b770d054349)
![Screenshot from 2023-05-30 18-18-54](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/17de50e6-9025-423f-9720-1710ec7334e5)
![Screenshot from 2023-05-30 18-19-04](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/93184cd7-821d-47bd-9c6f-de310cd4a6ee)
![Screenshot from 2023-05-30 18-19-09](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/4a2d7c2a-31ca-4c64-b924-8cd97806c2e4)
![Screenshot from 2023-05-30 18-19-21](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/59f17cb0-ec09-4cbe-97f6-9b102e37a165)
![Screenshot from 2023-05-30 18-19-23](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/4ce243ba-5e01-41eb-9e7a-3252d28252d8)
![Screenshot from 2023-05-30 18-19-27](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/c89efe02-4a7a-4c5b-a1d2-66b82d999c48)
![Screenshot from 2023-05-30 18-19-30](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/441e3c6e-380d-4d9d-b620-308df5d53197)
![Screenshot from 2023-05-30 18-19-34](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/a6f8a181-4d4f-404a-838f-06710d8737a7)
![Screenshot from 2023-05-30 18-19-37](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/c80529c2-f9cf-4fbb-a1cc-317099f792e5)
![Screenshot from 2023-05-30 18-19-41](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/b5c7853a-aee2-40ee-adc4-bfd1a3246ad2)
![Screenshot from 2023-05-30 18-19-45](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/505538db-be8f-4ad3-9d2e-7e3e61e430e3)
![Screenshot from 2023-05-30 18-19-49](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/f72e6859-8457-43a5-b02c-60077765b60e)
![Screenshot from 2023-05-30 18-19-53](https://github.com/harish-ragavendra-25/Ex-08-Data-Visualization-/assets/114852180/e0318794-f705-4360-b9b3-6c2ddba4c25b)

# RESULT:
thus the experiment executed sucessfully
