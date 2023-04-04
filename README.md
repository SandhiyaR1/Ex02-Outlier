# Ex02-Outlier
# AIM:

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
# ALGORITHM:
### STEP 1
Read the given Data.

### STEP 2
Get the information about the data.

### STEP 3
Detect the Outliers using IQR method and Z score.

### STEP 4
Remove the outliers.

### STEP 5
Plot the datas using Box Plot.

# PROGRAM:
```
DEVELOPED BY: SANDHIYA R, REGISTER NUMBER: 212222230129
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
### OUTPUT:
bhp.csv 
IQR METHOD
# df.head()
![image](https://user-images.githubusercontent.com/113497571/227278070-84105a5b-bf1e-43e6-bc58-e41ab5a4e5ce.png)


# df.describe()
![image](https://user-images.githubusercontent.com/113497571/227278136-84518f9b-9672-475d-ad5e-86b85bb3a485.png)


# df.info()
![image](https://user-images.githubusercontent.com/113497571/227278278-945aed75-3c99-4f7b-b4f8-4f4aff4ee7d7.png)


# df.shape
![image](https://user-images.githubusercontent.com/113497571/227278342-1c3f15ce-e159-4dd0-8f0d-c235e93e4784.png)


# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227278384-dd42f472-d6dd-40de-8e5e-3792d53cf34c.png)


# NEWDATA USING IQR
![image](https://user-images.githubusercontent.com/113497571/227278461-a4bc5bc0-732b-4a3f-9bd8-6d5a3c6b8e3e.png)


# OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227278521-8aab108c-2b86-458e-9dcf-95745db5b726.png)


# newdata.shape
![image](https://user-images.githubusercontent.com/113497571/227278607-817852e3-d940-4e04-9104-705cc96d9ed3.png)


# BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://user-images.githubusercontent.com/113497571/227278911-bef7f0b9-de23-4290-9642-1ab8140c8424.png)


# Zscore of 3
# NEWDATA USING Zscore
![image](https://user-images.githubusercontent.com/113497571/227279074-b61b657c-3c43-4611-b9d9-736f6232e43b.png)


# OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227279127-45d8c79d-ee01-40d1-b1a1-913f494ac075.png)


# newdata2.shape
![image](https://user-images.githubusercontent.com/113497571/227279235-e482c008-c8f3-4da7-8685-c6e9544ea819.png)

# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://user-images.githubusercontent.com/113497571/227279691-3b5119ec-9e2d-41c7-8b07-ad28167031d6.png)

# height_weight.csv
dataset.shape
![image](https://user-images.githubusercontent.com/113497571/227279829-23e4b4ed-b6d8-4493-8735-cefbe1516dec.png)


# dataset.describe()
![image](https://user-images.githubusercontent.com/113497571/227279975-07ccfc1b-cd88-4eba-a143-d7cbfb9595b5.png)

# dataset.info()
![image](https://user-images.githubusercontent.com/113497571/227280046-0ebfe466-a9ba-4400-a824-593b2d6445a0.png)


# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227280228-e7f0e7b8-c95a-466e-8153-fbcb3f24a7bf.png)


# HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227280343-4cad93e9-0295-4d01-965e-70bfa65f351a.png)


# DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227280389-5a4c3909-c6e9-4485-b4b5-ffbbadd2b12f.png)


# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227280427-076472c7-7aa1-495b-b640-fcd689bd3be1.png)


# WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227280476-b6665c7f-8032-4d07-98ca-c3b5afbd47a4.png)


# DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227280551-f61cc5b0-a5c1-4321-b11b-d1bb760cebcd.png)


# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497571/227280678-d18a3207-9528-403c-9edf-650b488c2d74.png)


### RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
