# NAME: PADMA SREE P
# REG NO:212224110032

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

# Coding and Output:
```
import numpy as np
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```
# OUTPUT:
<img width="1233" height="750" alt="Screenshot 2025-09-17 154222" src="https://github.com/user-attachments/assets/ec6d709e-2c37-4d87-9bc8-78e1407a935b" />

```
data.head(4)
```

# OUTPUT:
<img width="1103" height="220" alt="Screenshot 2025-09-17 154235" src="https://github.com/user-attachments/assets/4100f0a1-cb54-48d2-b316-b193dd463f4e" />

```
data.tail(7)
```

# OUTPUT:
<img width="1103" height="220" alt="Screenshot 2025-09-17 154235" src="https://github.com/user-attachments/assets/dcfe3549-2cdc-42fd-9720-950c58f13286" />

```
data.notnull()
```

# OUTPUT:
<img width="1210" height="691" alt="Screenshot 2025-09-17 154304" src="https://github.com/user-attachments/assets/becaace7-68d0-4888-a1c3-2e2e13964246" />

```
data.isnull().sum()
```

# OUTPUT:
<img width="1086" height="311" alt="Screenshot 2025-09-17 154319" src="https://github.com/user-attachments/assets/a929bf20-3d41-4376-9f56-ff2d3c872e5c" />

```
data.isnull().any()
```

# OUTPUT:
<img width="1249" height="323" alt="Screenshot 2025-09-17 154427" src="https://github.com/user-attachments/assets/6666294c-4ca3-411d-a4e6-656d5ca270ce" />

```
data.dropna(axis=1)
```

# OUTPUT:
<img width="1218" height="705" alt="Screenshot 2025-09-17 154438" src="https://github.com/user-attachments/assets/2918a00d-85a3-41d6-af88-72293b184b8f" />

```
data.dropna(axis=0)
```

# OUTPUT:
<img width="1232" height="471" alt="Screenshot 2025-09-17 154449" src="https://github.com/user-attachments/assets/de3bd163-c217-489d-889c-908d7c773cb4" />


```
data.fillna(0)
```

# OUTPUT:
<img width="1209" height="701" alt="Screenshot 2025-09-17 154500" src="https://github.com/user-attachments/assets/0abb334f-edc4-46e3-b0b7-dfa258f570f4" />


```
data.bfill()
```

# OUTPUT:
<img width="1239" height="699" alt="Screenshot 2025-09-17 154518" src="https://github.com/user-attachments/assets/ac0aa984-7c15-4f34-9404-779ff70fb7b5" />

```
data.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```

# OUTPUT:
<img width="1247" height="700" alt="Screenshot 2025-09-17 154530" src="https://github.com/user-attachments/assets/6afad6fd-f462-456e-b3b9-50552c346c9d" />

```
ir=pd.read_csv("iris.csv")
ir
```

# OUTPUT:
<img width="1215" height="467" alt="Screenshot 2025-09-17 154548" src="https://github.com/user-attachments/assets/9e4c7d82-9a23-4178-a5b5-26dd13528d30" />

```
ir.describe()
```

# OUTPUT:
<img width="1200" height="329" alt="Screenshot 2025-09-17 154558" src="https://github.com/user-attachments/assets/8af11f54-8066-4b8e-be27-c4dda2b274dc" />


```
import seaborn as sns
# sns.boxplot(x="sepal_width",data=ir)
```

# OUTPUT:
<img width="1214" height="610" alt="Screenshot 2025-09-17 154608" src="https://github.com/user-attachments/assets/788fa597-2f5e-41c4-afd8-07c48972343b" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
# OUTPUT:
<img width="1226" height="155" alt="Screenshot 2025-09-17 154620" src="https://github.com/user-attachments/assets/2a9451f0-d5cd-446d-aa8e-2b34197795d4" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```

# OUTPUT:
<img width="1202" height="216" alt="Screenshot 2025-09-17 154633" src="https://github.com/user-attachments/assets/effcc9d5-ac55-4071-b870-93fc2cdba434" />

```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```

# OUTPUT:
<img width="1215" height="493" alt="Screenshot 2025-09-17 154642" src="https://github.com/user-attachments/assets/aee9acd4-60d7-49a2-b601-f8edcc23b9f0" />

```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```

# OUTPUT:
<img width="1213" height="317" alt="Screenshot 2025-09-17 155028" src="https://github.com/user-attachments/assets/cb27a2af-b092-41eb-bd51-cc31ac1545d9" />

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```

# OUTPUT:
<img width="1253" height="359" alt="Screenshot 2025-09-17 155038" src="https://github.com/user-attachments/assets/4e5d01c5-04ff-4692-9115-3f00822e7fa7" />



# Result:
Thus the programs are executed successfully.
