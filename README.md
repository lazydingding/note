[![Analytics](https://ga-beacon.appspot.com/UA-80121379-2/notes-python)](https://github.com/lazydingding/note)


# Luping's Notes @ HKU

## Pandas

### Drop
#### Drop columns
```
df.drop(['col1','col2','Unnamed: 0'], axis=1, inplace=True)
```

### Group By
#### Group by & Sum
```
df = df.groupby(['col1','col2']).sum()
```
####  Sort, Group by and Extract the first row of the specific columns
```
df = df.sort_values(['col1','col2']).groupby('col1')['col1','col2'].first()
```

### Merge
#### Inner merge
```
df = pd.merge(df1, df2, how='inner')
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
```
