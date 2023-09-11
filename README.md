# Ex-04-Multivariate-Analysis

## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
## OUTPUT:

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/84114d90-ab3d-41e0-8eb7-1dea5aa90cc9)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/91db2ef4-1334-4b42-bbd0-568f766dde94)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/8b2f82d3-00af-4b06-baf3-a188159836c2)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/51439a25-f25e-4126-a6fc-df16b3556ddb)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/57d72b1b-ebfa-4c65-9fe8-b4bf9d54f978)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/0635dd76-2d83-44c6-9d9f-3ff3ebd3630a)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/17622760-529c-47cc-862e-13c1cee7e60c)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/2af4b7ed-4e22-40c4-b948-035e1e344ee1)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/1b2f645f-7108-4167-b196-b7dc0474fe8c)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/c8238eea-88dc-4e48-b504-10d447d2b85a)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/8852c0c9-60c4-41f5-acf6-288c7e75f664)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/a0442a7a-f39e-4280-8acc-de23d8aea462)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/6838e7f4-8f3e-40eb-acec-d637c705c62b)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/c2cbe674-0ab9-4cbd-b9b5-f3b02fd91fb9)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/75991f7b-1182-463a-ab73-16aa258d89a5)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/e5367e3b-04ee-4155-8d6a-01b5f8a0c3ca)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/35e48146-7e1d-4adb-80e3-df643fd7664d)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/a1db78c6-2abe-4298-959f-f29c03717491)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/2467733a-ee02-4df7-9f87-a78c754e9b6d)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/f7ecb362-eee8-4bc9-9983-478152a7677c)

![image](https://github.com/Yugendaran/Ex-04-Multivariate-Analysis/assets/128135616/612ac350-c74a-48a7-9b7e-ea83ad5c985e)


## RESULT:
Thus the program to perform EDA on the given data set is successfully executed.













