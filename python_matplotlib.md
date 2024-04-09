# Get axes
Normal way
```python
fig, ax = plt.subplots(1, 1, figsize=(17, 10))
```
One by one
```python
fig = plt.subplots(figsize=(17, 10))
# ax=fig.add_subplot(ROW,COLUMN,POSITION)
ax=f.add_subplot(1,N,i)
```

# Plot SVGs
```python
import matplotlib_inline.backend_inline
matplotlib_inline.backend_inline.set_matplotlib_formats('svg')
```
