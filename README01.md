## Pandas

1. axis=0 rows
2. axis=1 columns

```
df=pd.to_csv('sample.csv', names=['col1', 'col2', 'col3'], header=0, encoding='utf-8', skiprows=1, index_col=[0, 1], parse_date=True)
df.index=['ind0', 'ind1', 'ind2']
df.rename(columns={'col1': 'col10'})
df.sort_values(by='col1', ascending=False, na_position='first')
df.drop(['tagert'], axis=1) #delete target in columns
```
> multi_index by groupby()
```
df[['name','category','yen']].groupby(by=['name','category']).agg(['mean','sum','count','std','var']).round(0) 
df.pivot_table(index=['name'], columns='category', values=['yen','sales_yen'], aggfunc=['sum'], fill_value=0, margins=True, margins_name='ALL')
```
> merge to DataFrame
```
pd.merge(df1, df2, left_on='name', right_on='name', how='outer', indicator=True)
pd.merge(df1, df2, left_index=True, right_index=True, how='outer', indicator=True, sort=True)
pd.concat([df1, df2, df3, df4], axis=0, join='outer' )
```
> 欠損処理
```
df.isnull().sum() | df.info()

df.dropna()
df.fillna(0)
df.fillna(method = 'ffill')
df.fillna(df['data'].mean())
df.fillna(df['category'].mode()[0])
```
> create array of datetime
```
pd.date_range(start='2020/10/01', periods=30)
df['date'].apply(pd.to_datetime)
```
> preprosseing
```
pd.get_dummies(data=df, columns=['data'])
```

> month average
```
df_index_date.resample(freq='M').mean() # freq='W-SAT'

df.groupby(pd.Grouper(freq='M')).sum()
```
> plot to histgram and scatter 
```
from pandas.plotting import scatter_matrix
scatter_matrix(df)
```
