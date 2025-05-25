# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:

To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:

1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

Step 1: Import Libraries
Import necessary libraries: pandas for data handling and matplotlib.pyplot for visualization.

Step 2: Load the Dataset
Read the dataset from the provided CSV file.

Step 3: Explore the Dataset
Display the first few records using head().

Show information about data types and missing values using info().

Check for null values.

Step 4: Determine Optimal Number of Clusters (Elbow Method)
Use the K-Means algorithm with different values of k (from 1 to 10).

Compute and store Within-Cluster-Sum-of-Squares (WCSS) for each k.

Plot WCSS vs number of clusters to find the "elbow point".

Step 5: Apply K-Means Clustering with Optimal k=5
Fit the KMeans model with 5 clusters.

Predict the cluster for each data point.

Add the predicted cluster labels to the original dataset.

Step 6: Separate the Data into Clusters
Filter data points for each cluster into separate DataFrames.

Step 7: Visualize the Clusters
Plot the clusters using a scatter plot with different colors for each cluster.

Use "Annual Income (k$)" and "Spending Score (1-100)" as axes.


## Program:
```
Developed by: SRIDHARAN J
RegisterNumber: 212222040158


import pandas as pd

import matplotlib.pyplot as plt

data=pd.read_csv("/content/Mall_Customers (1).csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans

wcss=[]

for i in range(1,11):

kmeans=KMeans(n_clusters=i,init="k-means++")

kmeans.fit(data.iloc[:,3:])

wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)

plt.xlabel("No_of_Clusters")

plt.ylabel("wcss")

plt.title("Elbow Method")

km=KMeans(n_clusters=5)

km.fit(data.iloc[:,3:])

y_pred=km.predict(data.iloc[:,3:])

y_pred

data["cluster"]=y_pred

df0=data[data["cluster"]==0]

df1=data[data["cluster"]==1]

df2=data[data["cluster"]==2]

df3=data[data["cluster"]==3]

df4=data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")

plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")

plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")

plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")

plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")

plt.legend()

plt.title("Customer Segment")

```

## Output:

1.DATA.HEAD():


![Screenshot 2025-05-19 162225](https://github.com/user-attachments/assets/c80dc1f4-803a-43aa-8fc3-68dd95feec11)



2.DATA.INF0():


![Screenshot 2025-05-19 162232](https://github.com/user-attachments/assets/71e81e11-fd40-49b2-ac6a-c3e76043f49f)

3.DATA.ISNULL().SUM():

![Screenshot 2025-05-19 162237](https://github.com/user-attachments/assets/8c542c44-96ea-42d8-99a2-3aa3924a893f)


4.PLOT USING ELBOW METHOD:


![Screenshot 2025-05-19 162250](https://github.com/user-attachments/assets/c2fd8498-e5e1-4b41-927b-f8abf3c2485e)

5.Y_PRED ARRAY:

![Screenshot 2025-05-19 162301](https://github.com/user-attachments/assets/e7c4bb99-09ba-4132-92b0-96a61568dcb8)


6.CUSTOMER SEGMENT:

![Screenshot 2025-05-19 162310](https://github.com/user-attachments/assets/35016ff5-561c-405b-a619-fbf4be507de5)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
