# Multi row
## creation
```python
df_rows = [
  'row0',
  'row1'
  ]
df_cols = [
  'col0',
  'col1'
  ]
df = pd.DataFrame(columns=(df_rows+df_cols))
df.set_index(df_rows)
```
## adding new row
(with several cols values)
```python
In [27]: df.loc[('321', 4),['predicted_y', 'actual_y', 'predicted_full', 'actual_full']] =  (
           [20, 50, np.array((10, 20, 30), dtype='O'), [40, 50, 60]])

In [28]: df
Out[28]: 
                 predicted_y actual_y predicted_full   actual_full
subj_id org_clip                                                  
123     3                  2        5      [1, 2, 3]     [4, 5, 6]
321     4                 20       50   [10, 20, 30]  [40, 50, 60]
```
## slicing
https://stackoverflow.com/questions/53927460/select-rows-in-pandas-multiindex-dataframe
slice by 2nd level index
```python
df.query("two > 5")
```
slice a single 2nd level by match (e.g. close from ohlc)
take all 1st level, only take close and also drop 'close'
```
prices.stack().loc[(slice(None), slice('close')), :].droplevel(1)
```

# Multi col
## creation
Should be created with at least 1 column in advance
```python
df = pd.DataFrame(columns=[('idx0','idx0a'),('idx0','idx0b')])
df.columns = pd.MultiIndex.from_tuples(df.columns, names=['upper_level','lower_level'])
```
## adding new col
```python
df[symbol,'fee']=np.nan
df[symbol,'price']=np.nan
```
## adding row
```python
df.loc[today, (symbol,'fee')]   = val
```
## Move 1 col level up
```python
df.reset_index().set_index(['timestamp','symbol']).unstack(1).swaplevel(0,1, axis=1)
```
or with pivot
```python
cols=df.columns[df.columns != 'symbol']
df.reset_index().pivot(index='timestamp', columns = 'symbol', values=cols).swaplevel(0,1, axis=1)
```
## deleting top level index
```python
df.columns = df.columns.droplevel()
```
## slicing
Slice 2nd level and remove it
```python
df1=df.loc[:, (slice(None), 'close')]
df1.columns = df1.columns.droplevel(1)
```
