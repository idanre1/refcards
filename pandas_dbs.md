# csv
```python
df = pd.read_csv(csv, index_col=index_col, dtype='float')
# multi header cols
df = pd.read_csv(args.db, header=[0,1], index_col=0, parse_dates=True)
```

# hd5
```python
df.to_hdf(args.db, key='qos', complib='blosc', complevel=8)
```
