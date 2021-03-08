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

# Multi col
## creation
Should be created with at least 1 column in advance
```python
df = pd.DataFrame(columns=['idx0','idx0a'),('idx0','idx0b')])
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
