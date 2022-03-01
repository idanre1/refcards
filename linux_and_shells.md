# Linux terminal
## cycle through reverse-i-search in BASH
- <kbd>Ctrl</kbd> + <kbd>R</kbd>  
- `grep`  
- <kbd>Ctrl</kbd> + <kbd>R</kbd>  
- <kbd>Ctrl</kbd> + <kbd>S</kbd>  
- <kbd>Ctrl</kbd> + <kbd>R</kbd>  

---

# Linux shells
## Zsh
Complete https://devhints.io/zsh
## Bash
### Refcard
Complete https://devhints.io/bash  
If-Else https://linuxize.com/post/bash-if-else-statement/
### Brackets

```shell
if [ "$#" -ne 1 ]; then
    echo "Illegal number of parameters"
fi
```
OR
```shell
if test "$#" -ne 1; then
    echo "Illegal number of parameters"
fi
```
When in Bash, prefer using `[[ ]]` instead as it doesn't do word splitting and pathname expansion to its variables that quoting may not be necessary unless it's part of an expression.
```shell
if test [[ $# -ne 1 ]]; then
    echo "Illegal number of parameters"
fi
```
## sh (dash) refcard
http://eriklievaart.com/cheat/linux/shell/dash/dash.html
