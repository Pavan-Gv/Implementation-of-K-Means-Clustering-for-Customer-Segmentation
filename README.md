# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm

1.Import the required packages.
2.Import the dataset to work on.
3.From sklearn module import kmeans.
4.Define number of clusters to be made.
5.Assign the cluster values.
6.Plot the cluster using matplotlib.pyplot
7.End the program.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: G Venkata Pavan kumar
RegisterNumber: 212221240013
*/
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans

wcss = []
for i in range(1,11):
  kmeans = KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("no of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])

data["cluster"] =y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4= data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="blue",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="red",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="orange",label="cluster4")
plt.title("Customer Segment")
plt.legend()
```

## Output:
![M1](https://user-images.githubusercontent.com/94827772/173002895-c59c7ccd-7a94-4a93-9d83-ecbb32144bb6.png)
![M2](https://user-images.githubusercontent.com/94827772/173002892-c0c73627-5f21-4687-a432-20aa32b04d76.png)
![M3](https://user-images.githubusercontent.com/94827772/173002887-712c9321-2357-4cf4-b4eb-241272132a70.png)
![M4](https://user-images.githubusercontent.com/94827772/173002886-5fccf688-0c8f-45a8-a18b-d3c6dfaf70ba.png)
![M5](https://user-images.githubusercontent.com/94827772/173002876-57944844-2c0c-4de9-bbf3-b95b8b96c01e.png)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
