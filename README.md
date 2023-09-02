# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## Aim:
TO detect and remove the outliers in the given data set and save the final data.

## Algorithm:
Step 1
Import the required packages(pandas,numpy,scipy)

Step 2
Read the given csv file

Step 3
Convert the file into a dataframe and get information of the data.

Step 4
Remove the non numerical data columns using drop() method.

Step 5
Detect the outliers in the data set using z scores method.

Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7
Check if the outliersare removed from data set using graphical methods.

Step 8
Save the final data set into the file.

## Program:
```
FOR BHP.CSV FILE

import pandas as pd
df=pd.read_csv("/bhp.csv")
df
df.info()
df.shape
import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)]
print(newdata)
newdata=df[(df['price_per_sqft']>=lower) | (df['price_per_sqft']<=upper)]
print(newdata)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

FOR HEIGHT_WEIGHT.CSV FILE

import pandas as pd
df=pd.read_csv("/height_weight.csv")
df
df.info()
df.shape
df.describe()
import seaborn as sns
sns.boxplot(x="height",data=df)
Q1=df['height'].quantile(0.25)
Q3=df['height'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata1=df[(df['height']>=lower) | (df['height']<=upper)]
print(newdata1)
newdata=df[(df['height']>=lower) & (df['height']<=upper)]
print(newdata)
sns.boxplot(x='height',data=newdata1)
```
## OUTPUT:
#### Original data for bhp.csv file:
 
![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/e10bb3a9-b641-4ee7-9723-5d1d7984efdd)

#### Dataset information:
 
![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/38816f72-8267-4668-aebf-464ae59fd67d)

#### Shape of a data:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/72a124a8-9cd1-4569-ad2a-175e705614bb)

#### Box Plot of price_per_sqft column without outliers:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/5d30f29b-5895-4283-8a15-e5911b4a5273)

#### Removing the outlier for price_per_sqft column by using IRQ :

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/3315b091-1878-4bf7-af46-22b902dac0a3)

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/08eb1088-795a-4faa-9326-ee538b403456)

#### Box Plot of price_per_sqft column after IRQ:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/235388ed-c469-46d3-a453-49c7015f80c8)

#### Removing the outlier for price_per_sqft column by using zscore of 3 :

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/38140855-ea08-4740-93b0-5fd1d6930dd1)

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/567ca3e2-74cd-411f-abf7-24c3a9f482b7)

#### Box Plot of price_per_sqft column after zscore of 3:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/06ff570b-b0db-47ae-a8ab-b5146da18ebd)

#### Original data of height_weight.csv file for height:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/735932f9-58ed-446e-9d5a-5474a606af2c)

#### Dataset information:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/a6a5b7f0-56b6-4cd5-8472-271a755689c6)

#### Shape of a dataset:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/c330aa96-2008-4a4a-ac91-9ae30cf84894)

#### Box plot of height column without outlier:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/ecb98058-2e13-45ea-8a4c-e186beb1ac83)

#### Removing the outlier for height column by using IRQ :

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/9c8f342c-610f-48a7-8fa4-dbaf7880eeb3)

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/6f5e8c88-f43e-4e90-be5d-37e0d49580c1)

#### Box Plot of height column after IRQ:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/8169c62a-2ead-4ffd-99fd-9d8c5d6c6d06)

#### Original data of height_weight.csv file for weight:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/4a366a77-3856-4473-adbb-1417e92f92c9)

#### Dataset information:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/0300eb8e-8208-4339-a9b4-b71a93bf464b)

#### Shape of a dataset:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/5ce6ea82-696b-4855-b8ff-45cf26de0644)

#### Box plot weight column without outlier:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/30e09c44-6e26-4109-9ea9-08fa7b81363b)

#### Removing the outlier for weight column by using IRQ :

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/24f368e3-c310-4578-82c0-b2b2ab884715)

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/3ed556f5-eab2-4162-9f15-ef4d9cdca503)

#### Box Plot of height column after IRQ:

![image](https://github.com/Yuvaranithulasingam/ODD2023---Datascience---Ex-02/assets/121418522/f5acbd89-2880-4067-ac9e-5a71ccb87493)

## Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
