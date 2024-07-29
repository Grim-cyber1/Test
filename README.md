import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
import sklearn
import seaborn as sns
df = pd.read_csv("/content/1000_richest_people_in_the_world.csv")
df.head()
df.info()
df.shape
df.describe()
top_10_richest = df.nlargest(10,"Net Worth (in billions)")
top_10_richest

numeric_features = [ 'Net Worth (in billions)']
for feature in numeric_features:
    plt.figure(figsize=(10, 6))
    sns.histplot(df[feature], kde=True, bins=30)
    plt.title(f'Histogram of {feature}')
    plt.xlabel(feature)
    plt.ylabel('Frequency')
    plt.show()

plt.figure(figsize=(8,6))
industry_count = df['Industry'].value_counts()
sns.barplot(y=industry_count.index ,x=industry_count.values, palette='cividis')
sns.palplot(sns.color_palette("terrain_r", 10))
plt.title('')
plt.xlabel('Число людей')
plt.ylabel('Индустрия')
plt.show()

plt.figure(figsize=(15, 10))
sns.boxplot(data=df,x='Country',y='Net Worth (in billions)',hue='Industry')
plt.title('Net Worth Distribution by Country and Industry')
plt.xlabel('Country')
plt.ylabel('Net Worth (in billions)')
plt.legend(loc='upper right')
plt.show()
