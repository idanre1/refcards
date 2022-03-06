`parser = argparse.ArgumentParser()`

---

# Positional argument
## Required
`parser.add_argument("db" , help="")`  
`parser.add_argument("square", type=int) # must be int value`
## Optional
`parser.add_argument("db" , help="", nargs='?', default='/nas/pwned-passwords-sha1-ordered-by-count-v7.txt')`

# Non-positional argument
## Required
`parser.add_argument("-n", "--name", help="server_name")`  
`parser.add_argument("-v", "--verbosity", type=int, choices=[0, 1, 2]) # restrict choices`
## Optional
`parser.add_argument("--bridge", help="Bridge name", default='telegram', action='store')`  
`parser.add_argument("--verbosity", action='store_true') # true/false value`
## Counter
`parser.add_argument("-v", "--verbosity", action="count") # -vv counts for 2`  
`parser.add_argument("-v", "--verbosity", action="count", default=1) # -vv counts for 2, and the default is -v (a.k.a 1)`

---

`args = parser.parse_args()`
