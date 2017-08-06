[![Analytics](https://ga-beacon.appspot.com/UA-80121379-2/notes-python)](https://github.com/lazydingding/note)


# Luping's Notes @ HKU

## Pandas

### Read files
#### Read stata
```
df = pd.read_stata()
```

### Filter (Column)
#### Print columns out
```
print (list(df.columns))
```
#### Rename columns
```
df = df.rename(columns=lambda x: 'new_' + x)
```
#### Zfill
```
df['cusip'] = df['cusip'].str.zfill(9)
```
#### Column mean
```
df[df['col1'] == 'F'].col2.mean()
```
#### Column mean (multi conditions)
```
df[df['col1'].str.contains('str1') | df['col1'].str.contains('str2') | df['col1'].str.contains('str3')].col2.mean())
```
#### Split Column
```
df['col1'] = df['col1'].str.split(':').str.get(1)
df['col1'] = df['col1'].astype('str').str[:4]
```

### Filter (Row)
#### Keep the rows that meet the condition
```
df = df[df['col1'] == i]
```
#### Unique rows
```
df['col1'].unique()
```

### Merge & Concat & Append
#### Concat (ingore index)
```
df = pandas.concat([df1, df2], ignore_index=True)
```
#### Append
```
df = df.append(df1, ignore_index=True)
```
#### Inner merge
```
df = pd.merge(df1, df2, how='inner')
```
#### Reset Index
```
df = df.reset_index(drop=True)
```

### Group By
#### Group by & Sum (A column)
```
df['col1'] = df.groupby(['col2','col3'])['col1'].transform('sum')
```
#### Group by & Sum (Keep all of the DataFrame)
```
df = df.groupby(['col1','col2']).sum()
```
#### Group by & Max
```
df = df.groupby(['col1','col2']).max()
df = df.groupby(['col1','col2']).transform('max')
```
#### The group-by key disappeared after grouping by
````
df = df.groupby(['col1','col2']).sum().reset_index()
````
#### Sort, Group by and Extract the first row of the specific columns
```
df = df.sort_values(['col1','col2']).groupby('col1')['col1','col2'].first()
```

### Drop
#### Drop duplicates
```
df = df.drop_duplicates()
```
#### Keep duplicates
```
df = pd.concat(g for _, g in df.groupby(['col1','col2']) if len(g) > 1)
```
#### Drop columns
```
df.drop(['col1','col2','Unnamed: 0'], axis=1, inplace=True)
```

### Write
#### Write to .csv without index
```
df.to_csv('o.csv', index=False, encoding='utf-8')
```



## Datetime
#### Create a single datetime
```
from datetime import datetime
datetime.strptime("16:00:00", "%H:%M:%S")
```
#### Time for + / - / compare
```
from datetime import timedelta
timedelta(minutes=60)
```
#### Column to datetime format
```
df['time_datetime'] =  pd.to_datetime(df['time_string'], format='%H:%M:%S')
df['time_datetime'] =  pd.to_datetime(df['time_string'], format='%d-%b-%y') e.g.12-Sep-87
```

## 赋值
```
df.loc[index, 'col1'] = 1 much better than df['col1'][index] = 1
```
