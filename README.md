# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df = pd.read_csv('/content/SAMPLEIDS.csv')
df
 ```
![Screenshot 2024-02-27 153950](https://github.com/gokulapriya632202/exno1/assets/119560302/204785d6-4268-4cb6-ada8-66efad1e69c9)

 ```
 df.head(5)
 ```
![Screenshot 2024-02-27 154446](https://github.com/gokulapriya632202/exno1/assets/119560302/2b55ecb8-b3ee-404c-9b94-01df5cc33c40)

```
df.tail(5)
```
![Screenshot 2024-02-27 154904](https://github.com/gokulapriya632202/exno1/assets/119560302/27efb079-6032-489a-b429-89d1c4d66ef5)

```
df.info()
```
![Screenshot 2024-02-27 155000](https://github.com/gokulapriya632202/exno1/assets/119560302/00a2f368-b2b8-41d6-9541-c9b35139ddce)

```
df.describe()
```
![Screenshot 2024-02-27 155117](https://github.com/gokulapriya632202/exno1/assets/119560302/e27d4cc2-75b8-45e1-afb1-cf9f6678713d)

```
df.shape
```
![Screenshot 2024-02-27 155227](https://github.com/gokulapriya632202/exno1/assets/119560302/034a2ab8-b2e0-410a-bf5d-c9b1bb422c6a)

 ```
 df.isnull().sum()
 ```
![Screenshot 2024-02-27 155323](https://github.com/gokulapriya632202/exno1/assets/119560302/cb235ece-3b45-4d80-9f9a-34617abc2195)

```
df.nunique()
```
![Screenshot 2024-02-27 155356](https://github.com/gokulapriya632202/exno1/assets/119560302/57ec0153-e4ef-4f12-9a39-6a27ec4dc470)

```
mn=df.TOTAL.mean()
mn
```
![Screenshot 2024-02-27 155459](https://github.com/gokulapriya632202/exno1/assets/119560302/a75edc13-e0b1-40fd-b602-15cfc4c0de1e)

```
df['GENDER'].value_counts()
```
![Screenshot 2024-02-27 155538](https://github.com/gokulapriya632202/exno1/assets/119560302/47118939-2bbc-4f6a-b28a-71d479ae8e6d)

```
df.TOTAL.fillna(mn,inplace=True)
df.M4.fillna(0)
```
![Screenshot 2024-02-27 155629](https://github.com/gokulapriya632202/exno1/assets/119560302/048b7aa2-2441-49e7-be5f-213322349139)

 ```
 min=df.M4.min()
 min
 ```
![Screenshot 2024-02-27 160141](https://github.com/gokulapriya632202/exno1/assets/119560302/6038638c-229d-423b-9a46-5cb5dd57a5ce)
```
df.M4.fillna(min,inplace=True)
df
```
![Screenshot 2024-02-27 160738](https://github.com/gokulapriya632202/exno1/assets/119560302/5216d1a3-ccdb-4a46-9620-1d06120a6c0c)

```
df.isnull()
```
![Screenshot 2024-02-27 160841](https://github.com/gokulapriya632202/exno1/assets/119560302/b46545d5-50e2-4b0f-8a80-907161accf11)

```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![Screenshot 2024-02-27 160952](https://github.com/gokulapriya632202/exno1/assets/119560302/803c0cf3-d655-4e45-b5d9-bb9744eba5af)

```
sns.boxplot(data=af)
```
![Screenshot 2024-02-27 161157](https://github.com/gokulapriya632202/exno1/assets/119560302/baadee08-6544-476e-99a3-9f34977a61d4)

```
sns.scatterplot(data=af)
```
![Screenshot 2024-02-27 161241](https://github.com/gokulapriya632202/exno1/assets/119560302/917fc7bc-621d-4e77-bc06-9857c700a5bb)

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2024-02-27 161326](https://github.com/gokulapriya632202/exno1/assets/119560302/87a31542-0501-4535-965f-78a98fe33c48)

```
low=q1-1.5*iqr
low
```
![Screenshot 2024-02-27 161405](https://github.com/gokulapriya632202/exno1/assets/119560302/fdeed5c2-01fe-45e4-bbfa-3ee0396527bf)

```
high=q3+1.5*iqr
high
```
![Screenshot 2024-02-27 161440](https://github.com/gokulapriya632202/exno1/assets/119560302/cfaafb3f-2578-490b-bfc1-0d19593b935a)

```
af=af[((af>=low)&(af<=high))]
af
```
![Screenshot 2024-02-27 161523](https://github.com/gokulapriya632202/exno1/assets/119560302/8cef3588-15b9-42c2-a52f-f61da1db2cbf)

```
af.dropna()
```
![Screenshot 2024-02-27 161559](https://github.com/gokulapriya632202/exno1/assets/119560302/697716fd-3782-4951-8ffb-55b12ecdfc1f)

```
sns.boxplot(data=af)
```
![Screenshot 2024-02-27 161631](https://github.com/gokulapriya632202/exno1/assets/119560302/59b2ddb5-0039-4772-8150-6706789e68fb)

```
data=[1,12,15,18,21,24,27,20,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]
df=pd.DataFrame(data)
df
```
![Screenshot 2024-02-27 161753](https://github.com/gokulapriya632202/exno1/assets/119560302/4e580f15-cbd3-4d6c-bf80-59f7efed80d8)

```
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
z
```
![Screenshot 2024-02-27 165118](https://github.com/gokulapriya632202/exno1/assets/119560302/06e6135a-05ad-459b-be52-abba2647c31a)


# Result
         Thus, we read the given data and perform data cleaning and save the cleaned data to a file.
