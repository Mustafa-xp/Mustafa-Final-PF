# Mustafa-Final-PF

PF project ( GPU data analysis )  

import pandas as pd
df = pd.read_csv(r"gpu data.csv")
df.shape

## Data Cleaning
df.info()
### Columns
column = list(df.columns)
column
##### Check Empty values
df.isna().sum()
#### Cleaning empty set
df.dropna
df.dropna(inplace=True)

## Replace Empty values
df.fillna(17)
### Replace specific columns
df['Name'].fillna(48)
### Mean,Mode,Median
df['3DMARK'].mean() # the code wont be able to find the average if there's a non numerical number.
df['VRAM'].mode()  # Common
df['3DMARK'].median()  # middle (doesnt calculate the middle one if any value is non numerical or commas are present)

## Data Duplications
df.duplicated()
#### Drop 
df.drop_duplicates()
#### Describe
df.describe()
#### iloc
df.describe(include = "all").iloc[[0,6]] # includes all and tell the index and positions
#### loc
df.describe(include = "all").loc[["min","max"]] # includes all and tell the minimum and maximum values

## Adding a column
df['col'] = 4
df
## Remove a column
df.drop(columns=['col'], inplace=True, errors='ignore')
df
## Adding a row
a = {
    'Name': 'New GPU',  
    'Wattage': 200,           
    'VRAM': 12,              
    '3DMARK': 15000,          
}
df = pd.concat([df, pd.DataFrame([a])], ignore_index=True)
df
## Remove a row
df.drop(50,inplace=True) # it removed my 0,50,51 and 53 index
df

## Slicing 
df[1:7]
df[2:20:3]
### columns slicing
df[2:20:3]

## Flowcharts
df['VRAM'].value_counts().plot(kind="bar")
df['Name'].value_counts().plot(kind="barh")
df['Wattage'].value_counts().plot(kind="box")
df['3DMARK'].value_counts().plot(kind="density")
df['Name'].value_counts().plot(kind="pie")
df['VRAM'].value_counts().plot(kind="line")
df['Wattage'].value_counts().plot(kind="kde")
df['3DMARK'].value_counts().plot(kind="hist")

## Data Aggretion
df[['Name', '3DMARK']].aggregate(['sum', 'min'])
#### sum()
df['3DMARK'].sum()
#### std() (Standard Deviation)
df['3DMARK'].std()
#### var() Variance Calculation
df['3DMARK'].var()

## Data Preprocessing
df.isnull().sum() # it only shows the empty values and taking the sum of the dataframe
#### rename() Rename Columns
df.rename(columns={'Name': 'Variant'}, inplace=True)
df

## Data Saving

df = pd.read_csv("gpu data.csv")

df.to_excel("final project.xlsx", index=False)
