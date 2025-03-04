## Name: Samakash R S
## REG NO: 212223230182
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
#                                                                      DATA CLEANING
```python
import pandas as pd
import random
import numpy as np
df = pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2025-03-04 104129](https://github.com/user-attachments/assets/56b1b83d-fb29-4498-8da3-b2f8979cf8f4)
```python
df.tail()
```
![Screenshot 2025-03-04 104238](https://github.com/user-attachments/assets/c6f76758-906f-4533-aca0-7675c00bf690)
```python
df.head()
```
![Screenshot 2025-03-04 104348](https://github.com/user-attachments/assets/197fedb6-5fda-494c-9dca-61ddc6121789)
```python
df.fillna(1)
```
![image](https://github.com/user-attachments/assets/063b281e-0a00-4780-87e3-37d52015eada)
```python
df.isnull().sum()
```
![Screenshot 2025-03-04 104515](https://github.com/user-attachments/assets/37c15276-8e67-462b-abc4-b3bfa7b39f74)
```python
df.isnull().any()
```
![Screenshot 2025-03-04 104645](https://github.com/user-attachments/assets/247b83a4-89e8-4399-8ca5-cdccfa18f9ec)
```python
df.dropna()
```
![Screenshot 2025-03-04 104721](https://github.com/user-attachments/assets/19c1bfe7-8a32-490f-a24d-ffb362f89d8e)
```python
df.fillna(method="ffill")
```
![Screenshot 2025-03-04 104813](https://github.com/user-attachments/assets/1f78ee12-c255-4c06-9542-a32116cb4953)
```python
df.fillna(method="bfill")
```
![Screenshot 2025-03-04 104911](https://github.com/user-attachments/assets/56f2bff9-8875-495a-baf8-f75088c780fc)
```python
df.fillna({'GENDER':'MALE','NAME':'SAM','ADDRESS':'CHENNAI','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-04 105001](https://github.com/user-attachments/assets/9cd44ebe-0b31-42ba-a94d-2b7a795217f1)

#                                                                    IQR(INTER QUARTILE RANGE)

```python
import pandas as pd
ir = pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/f74dd2c7-feb1-4319-bd57-8f66b015ef7f)
```python
ir.describe()
```
![Screenshot 2025-03-04 105406](https://github.com/user-attachments/assets/0a6f360a-273e-465a-856a-fda0de8e7ac8)
```python
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2025-03-04 105533](https://github.com/user-attachments/assets/91567439-71c7-4d70-bb33-84b064722a84)
```python
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![Screenshot 2025-03-04 105613](https://github.com/user-attachments/assets/be2a2194-6eb2-4622-a4e4-180e64dd40b7)
```python
rid = ir[(ir.sepal_width < c1-1.5*iq) | (ir.sepal_width > c3+1.5*iq)]
rid['sepal_width']
```
![Screenshot 2025-03-04 105646](https://github.com/user-attachments/assets/306298db-6ac3-473a-90db-a9f7513b1f29)
```python
delid = ir[~((ir.sepal_width < (c1-1.5*iq)) | (ir.sepal_width > (c3+1.5*iq)))]
delid
```
![Screenshot 2025-03-04 105907](https://github.com/user-attachments/assets/687e9b16-9b56-44fc-b617-e5ce1e5368f5)
```python
sns.boxplot(x='sepal_width',data=delid)
```
![Screenshot 2025-03-04 105954](https://github.com/user-attachments/assets/3aa8463f-34a6-43a7-866d-0d19728d1f6b)
```python
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![Screenshot 2025-03-04 110033](https://github.com/user-attachments/assets/8f4b06c2-edfd-46da-ab51-c9d6944399fb)
```python
z = np.abs(stats.zscore(dataset['height']))
z
```
![Screenshot 2025-03-04 110123](https://github.com/user-attachments/assets/43c9e274-939b-4c37-80ca-ef3ce40ba9bb)


# Result
Thus We have cleaned the data and remove the outliers by detection using IQR and Z-score method.
