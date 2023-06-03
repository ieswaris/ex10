#  Ex10 Data Science Process on Complex Dataset

# AIM

To Perform Data Science Process on a complex dataset and save the data to a file.

# ALGORITHM
# STEP 1

Read the given Data

# STEP 2

Clean the Data Set using Data Cleaning Process

# STEP 3

Apply Feature Generation/Feature Selection Techniques on the data set

# STEP 4

Apply EDA /Data visualization techniques to all the features of the data set

# PROGRAM

```
import pandas as pd
import numpy as np
import seaborn as sns
from google.colab import files
uploaded = files.upload()
df = pd.read_csv("world_pop.csv")
print(df.isnull().sum())

df = df.drop_duplicates()


df = df.fillna(0)


cols_to_keep = ['country', 'year_1960', 'year_1970', 'year_1980', 'year_1990', 'year_2000', 'year_2010', 'year_2020']
df_selected = df[cols_to_keep].copy()

df_selected['Average_Growth_Rate'] = df_selected.iloc[:, 1:-1].mean(axis=1).pct_change() * 100

df_selected['Total_Population'] = df_selected.iloc[:, 1:].sum(axis=1)

plt.figure(figsize=(10, 6))
years = df_selected.columns[1:-2]
total_population = df_selected[years].sum()
plt.bar(years, total_population)
plt.xlabel('Year')
plt.ylabel('Population')
plt.title('Population Over the Years')
plt.xticks(rotation='vertical')
plt.show()


plt.figure(figsize=(10, 6))
years = df_selected.columns[1:-2]
average_population = df_selected[years].mean()
plt.plot(years, average_population, marker='o')
plt.xlabel('Year')
plt.ylabel('Average Population')
plt.title('Average Population Over the Years')
plt.xticks(rotation='vertical')
plt.show()
df_selected['Total_Population_2020'] = df_selected['year_2020']
top_10_countries = df_selected.nlargest(10, 'Total_Population_2020')
plt.figure(figsize=(10, 6))
sns.barplot(x='Total_Population_2020', y='country', data=top_10_countries, palette='viridis')
plt.xlabel('Population in 2020')
plt.ylabel('Country')
plt.title('Top 10 Countries by Population in 2020')
plt.show()
```
# OUTPUT
![image](https://github.com/ieswaris/ex10/assets/127847210/a52986db-cc2d-4b2f-8f36-7772d08e0a10)

![image](https://github.com/ieswaris/ex10/assets/127847210/10ce82ce-1109-46cf-b0c3-e46a301aefb8)

![image](https://github.com/ieswaris/ex10/assets/127847210/351c1ee3-2381-4bc9-be08-364aa598b3bc)

# RESULT

Thus, to Perform Data Science Process on a complex dataset and save the data to a file has been performed successfully.

