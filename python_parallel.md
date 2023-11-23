# Serial code
```python
d = {}
for t in tqdm(tests):
    df_=df.loc[t]
    mean_a = df_['a'].mean()
    mean_b = df_['a'].mean()
    d[t] = a,b
result.columns=['a', 'b']
result=pd.DataFrame(d).T
```
# Parallel code
```python
from fastcore.parallel import parallel
def f(t):
    df_=df.loc[t]
    mean_a = df_['a'].mean()
    mean_b = df_['a'].mean()
    return a,b
result=pd.DataFrame(parallel(f, tests, progress=True),
                    index=tests, columns=['a', 'b']
                    )
```
