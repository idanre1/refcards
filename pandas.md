# Remove only rows with all values NaN
```python
df = df.dropna(axis = 0, how = 'all')
```
# Convert series to integers
Series
```python
pd.to_numeric(ser, errors='coerce').fillna(0).astype(int)
```
DataFrame
```python
df.apply(pd.to_numeric, errors='coerce', axis=1).fillna(0).astype(int)
```
