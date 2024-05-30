data = pd.read_csv("/kaggle/input/online-sales-data/Online Sales Data.csv")
df = pd.DataFrame(data)
print(df.head(10))

df = df.drop_duplicates()
print(df.isnull().sum())
df['Date']= pd.to_datetime(df['Date'])
print(df.dtypes)


print(df.describe())
print("\n")
print(df.columns)
print("\n")
print(df['Product Category'].value_counts(ascending=False))
print("\n")
print(df['Product Name'].value_counts(ascending=False))
print("\n")
print(df.nunique())


import matplotlib.pyplot as plt
import seaborn as sns
plt.figure(figsize=(12,6))
sns.lineplot(data = df, x='Date', y='Units Sold')
plt.title('Sales OVER Date')
plt.xlabel('Date')
plt.ylabel('Units Sold')
plt.show()

plt.figure(figsize=(12,6))
sns.barplot(data=df, x='Product Category', y='Units Sold')
plt.title('Sales OVER Category')
plt.xlabel('Category')
plt.ylabel('Units Sold')
plt.show()

plt.figure(figsize=(12,6))
sns.histplot(df['Units Sold'], bins=10, kde=True)
plt.title('Sales Distribution')
plt.xlabel('sales')
plt.ylabel('Frequency')
plt.show()

plt.figure(figsize=(12,6))
sns.countplot(data=df, y='Region',order = df['Region'].value_counts().index)
plt.title('Count of products by Regions')
plt.xlabel('Count')
plt.ylabel('Regions')
plt.show()
