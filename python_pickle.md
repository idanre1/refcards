# Write
```python
import pickle
dumpname='filename'
with open(f'{dumpname}.pickle', 'wb') as f:
  pickle.dump(my_object, f)
```
# read
```python
with open(f'{dumpname}.pickle', 'rb') as f:
  loaded_object = pickle.load(f)
```
# freeze python
```sh
mkdir freeze
python --version > freeze/pyver.freeze
pip freeze -l > freeze/venv.freeze
```
