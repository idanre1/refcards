# Actions with checkouts
Merge without commit
```bash
git merge --no-commit <HASH>
```
Cherry pick without commit
```bash
git cherry-pick -n <HASH>
```
# Replay the last N git commits on a different branch
```bash
git rebase -p --onto master testing~10 testing
```
This will apply the last ten commits from *testing* to *master*.  
The last 10 commits on testing will remain **orphaned**
```bash
-p or --preserve-merges
```
This option tells Git to preserve merge commits during the rebase process. Normally, rebase flattens the commit history, but with this option, merge commits are kept intact.
# submodules
Update sub modules
```bash
git submodule update --init --recursive
```
