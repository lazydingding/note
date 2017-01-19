[![Analytics](https://ga-beacon.appspot.com/UA-80121379-2/notes-python)](https://github.com/lazydingding/note)


# Luping's Notes @ HKU

## Pandas
#### Drop columns
```
df.drop(['col1','col2','Unnamed: 0'], axis=1, inplace=True)
```
#### Group by & Sum
```
df = df.groupby(['col1','col2']).sum()
```
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
