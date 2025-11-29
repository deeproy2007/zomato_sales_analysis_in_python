# Project Overview

This project contains a Jupyter Notebook (`main.ipynb`) with the
following elements:

## Code Cell

``` python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
plt.style.use('seaborn-v0_8')
```

## Code Cell

``` python
df=pd.read_csv('zomato.csv',encoding='latin-1')
print(df.head())
```

## Code Cell

``` python
print("num of row",df.shape[0])
print("num of column",df.shape[1])
df.info()
```

## Code Cell

``` python
df.describe(include='all')
```

## Code Cell

``` python
df.isnull().sum()
```

## Code Cell

``` python
print("Duplicate :",df.duplicated().sum())
```

## Code Cell

``` python
df=df.drop_duplicates()
print(df.duplicated().sum())
```

## Code Cell

``` python
df['Country Code'].unique()
```

## Code Cell

``` python
if 'Cuisines' in df.columns:
     top_cui=df['Cuisines'].value_counts().head(10)
     plt.figure(figsize=(10,6))
     sns.barplot(x=top_cui.values,y=top_cui.index,palette='viridis')
     plt.title("Top 10 Cuisines")
     plt.xlabel("number of restaurants")
     plt.ylabel("Cuisines Type")
     plt.show()
```

## Code Cell

``` python
plt.figure(figsize=(10,6))
sns.histplot(df["Aggregate rating"],bins=20,kde=True,color='orange')
plt.title("Distribution of restaurend rating")
plt.xlabel("")
plt.show()
             
```

## Code Cell

``` python
if 'City' in df.columns:
  avg_rating_city=df.groupby('City')['Aggregate rating'].mean().sort_values(ascending=False).head(10)
  plt.figure(figsize=(12,6))
  sns.barplot(x=avg_rating_city.values,y=avg_rating_city.index,palette="coolwarm")
  plt.show()
```

## Code Cell

``` python
Delivery=df['Has Online delivery'].value_counts()
plt.figure(figsize=(10,6))
plt.pie(Delivery,labels=Delivery,autopct="%1.1f%%",startangle=90,colors=['red','orange'])
plt.title("Online Delivery Availability")
plt.show()
```

## Code Cell

``` python
total_booking = df['Has Table booking'].value_counts()

plt.figure(figsize=(6,6))
plt.pie(
    total_booking,
    labels=total_booking.index,
    autopct="%1.1f%%",
    startangle=90,
    colors=['green', 'orange'],
    wedgeprops={'edgecolor': 'black'}
)

plt.title("Table Booking Distribution")
plt.show()

```

## Code Cell

``` python
#votes and ratings
plt.figure(figsize=(10,6))
sns.scatterplot(x='Votes', y='Aggregate rating', data=df, color='purple')
plt.title('Votes vs Ratings')
plt.xlabel('Number of Votes')
plt.ylabel('Aggregate Rating')
plt.show()
```

## Code Cell

``` python
top_cui=df['Cuisines'].value_counts().head(10)
plt.figure(figsize=(10,6))
sns.barplot(x=top_cui.values,y=top_cui.index,palette='viridis')
plt.title("Top 10 Cuisines")
plt.xlabel("number of restaurants")
plt.ylabel("Cuisines Type")
plt.show()
```

## Code Cell

``` python
Cuisines_wise=df['Cuisines'].value_counts().head(5)
plt.figure(figsize=(10,6))
myexplode=[0,0,0.2,0,0]
plt.pie(Cuisines_wise,labels=Cuisines_wise,autopct="%1.1f%%",explode=myexplode,startangle=90)
plt.show()
```

## Code Cell

``` python
```

------------------------------------------------------------------------

Generated automatically.
