
```
df=pd.to_csv('sample.csv', names=['col1', 'col2', 'col3'], header=0, encoding='utf-8', skiprows=1, index_col=[0, 1], parse_date=True)
df.index=['ind0', 'ind1', 'ind2']
df.rename(columns={'col1': 'col10'})
```
