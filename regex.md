# playground
https://regex101.com/
# findall
```python
import re

txt = "The rain in Spain"
x = re.findall("^The.*Spain$", txt) 
  ['The rain in Spain']
```
# compiled regex
```python
import re

txt = "adfafad (Mssnnd) (ABC) (DEF)"
comp_reg = re.compile("\(([A-Z]+)\)$")
x = comp_reg.findall(txt) 
  ['DEF']
```
