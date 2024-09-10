Exno:1
Data Cleaning Process
AIM

To read the given data and perform data cleaning and save the cleaned data to a file.
Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.
Algorithm

STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers
Coding and Output:
Data cleaning process:

import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df

image

df.head()

image

df.tail(5)

image

df.isnull()

image

df.notnull()

image

df.dropna(axis=0)

image

df.dropna(axis=1)

image

df.fillna(0)

image

print(df.shape)

image
IQR:

import pandas as pd
import seaborn as sns
ir=pd.read_csv('/content/iris.csv')
ir

359434303-5f92ae1d-167b-4412-8e99-312c878199d7

ir.describe()

image

sns.boxplot(x='sepal_width',data=ir)

image

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

image

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

image

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

image

sns.boxplot(x='sepal_width',data=delid)

image
Z SQUARE

import matplotlib.pyplot as plt
import pandas as pd
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset

image

df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr

image

low = q1 - 1.5*iqr
low

image

high = q3 + 1.5*iqr
high

image

df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1

image

z = np.abs(stats.zscore(df['height']))
z

image

 df1 = df[z<3]
 df1

image
Result

Thus the Data Cleaning Process and Detecting and Removal of Outliers is executed successfully.
