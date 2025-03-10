## NAME:SUJITHRA.K
## REGISER NUMBER:212223040212
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
          import numpy as np
          import seaborn as sns
          import os 
          df=pd.read_csv("SAMPLEIDS.csv")
          df
```
![418845626-ac94080a-8b8b-4993-b88f-fc5f11015ea4](https://github.com/user-attachments/assets/e54dbef3-955e-46d7-8c13-15b1ee67154e)

```
         df.isnull().sum()
```
![418846419-94400342-1c3a-4d8d-86a7-9077d6f39b09](https://github.com/user-attachments/assets/3aa9d8e8-2296-4a2a-8865-4e921fbd814c)
```
         df.isnull().any()
```
![418846644-a257a60d-a429-4569-997f-f031f6499aa6](https://github.com/user-attachments/assets/f7424760-acfa-4778-8d2d-a10e4839ccb0)
```
         df.dropna()
```

![418847050-edb3367d-6dbb-46d7-adbc-0d8fa1d023f3](https://github.com/user-attachments/assets/619a4bd3-845a-40fc-9a9a-232908346f98)
```
         df.fillna(0)
```
![418847314-de591f57-efb5-447b-b591-1ee7c2274000](https://github.com/user-attachments/assets/1781246b-917b-42ae-b7b5-8c5264c39d1a)
```
         df.fillna(method = 'ffill')
```

![418847649-5060093f-e8f8-4ddd-8392-c4a4a62955b3](https://github.com/user-attachments/assets/30debd4b-b177-4061-9035-69faab22e0a4)
```
         df.fillna(method = 'bfill')
```
![418847925-2955f31e-bd58-4fa8-be56-ccb274f47439](https://github.com/user-attachments/assets/a6289b54-bba0-4b62-af5b-004c9b071c8d)
```
         df_dropped = df.dropna()
           df_dropped
```
![418848412-3289eb51-454a-45de-a9a0-7e5f26049126](https://github.com/user-attachments/assets/1b9c9973-dfd6-4657-b03d-1fc8dd06c790)
```
         df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![418848636-c1361b56-6d4d-44c7-b9b5-41c8262f143e](https://github.com/user-attachments/assets/d7615af1-19ae-4465-b0bf-8018b0ad95a1)

```
         import pandas as pd
         
         ir=pd.read_csv('iris.csv')
         ir
```
![418849104-9071e7c2-ed41-4a26-9e8b-4ce9a9fa828d](https://github.com/user-attachments/assets/82823e0a-6f30-47e0-a3a9-f0b27add8732)
```
         ir.describe()
```

![418849316-e33721cb-1eda-4371-b2ee-3447a4e11593](https://github.com/user-attachments/assets/24ab59dd-bf00-4653-b848-efb7bab651ce)
```
         import seaborn as sns
         
         sns.boxplot(x='sepal_width',data=ir)
```
![418849581-9baa2f04-556a-45ec-b5e7-d27750f4add7](https://github.com/user-attachments/assets/1224262e-9f5c-4799-a2b9-7979d9cbe12d)
```
           c1=ir.sepal_width.quantile(0.25)
           c3=ir.sepal_width.quantile(0.75)
           iq=c3-c1
           print(c3)
```
3.3
```
            rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            rid['sepal_width']
```
![418850000-ee76115a-0579-481a-aea9-6f543128e6fb](https://github.com/user-attachments/assets/2f6fe7dc-3451-4434-9145-a43e4a48787e)
```
            delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            delid
```

![418850122-7ce4a415-b73c-432f-8aa7-8456fcd464a5](https://github.com/user-attachments/assets/20c02842-3741-46ea-8bc2-a2e58279c64a)
```
           sns.boxplot(x='sepal_width',data=delid)
```
![418850360-b77cbb9a-1515-4dc0-9f4e-37e31def4071](https://github.com/user-attachments/assets/0ec0c93f-baca-4891-bd78-a99be25da736)
```
            import matplotlib.pyplot as plt
            import pandas as pd
            import numpy as np
            import scipy.stats as stats

            dataset=pd.read_csv("heights.csv")
            dataset
```


![418850753-e45fdc5c-9aab-4166-a43a-5db2e7fff711](https://github.com/user-attachments/assets/04b7f90e-b744-4739-a0b4-38f4d56174d9)
```
            df = pd.read_csv("heights.csv")
            q1 = df['height'].quantile(0.25)
            q2 = df['height'].quantile(0.5)
            q3 = df['height'].quantile(0.75)
            
            iqr = q3-q1
            iqr
```
0.9249999999999998
```
  low = q1 - 1.5*iqr
        low
```
3.8625000000000003

```
        high = q3 + 1.5*iqr
        high
```
7.5625
```
        df1 = df[((df['height'] >=low)& (df['height'] <=high))]
        df1
```

![418851558-b0d039ac-5d74-4d1d-82b6-e17fb446d82b](https://github.com/user-attachments/assets/f6689c34-e151-4ad7-a734-cf3060374858)
```
        z = np.abs(stats.zscore(df['height']))
        z
```
![418851732-8cc50a8c-aca8-4c09-8539-de026443135d](https://github.com/user-attachments/assets/856010e7-9d2b-4c7e-8e7a-5d588d78bd48)
```
        df1 = df[z<3]
        df1
```

![418852183-ab066131-c05d-407b-a25a-17245d160034](https://github.com/user-attachments/assets/ed721523-dca2-43ca-95b1-a89be1bf9f85)

## RESULT

Thus the given data  successfully performed data cleaning and saved the cleaned data to a file.        














            

