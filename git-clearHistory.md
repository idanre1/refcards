# Brute force
```
# Remove the history from  
rm -rf .git  

# Recreate the repos from the current content only  
git init  
git checkout -b main  
git add .  
git commit -m "Initial commit"  

# push to the github remote repos ensuring you overwrite history  
git remote add origin git@github.com:<YOUR ACCOUNT>/<YOUR REPOS>.git  
git push -u --force origin main  
```

# On single branch
```
git checkout --orphan newBranch
git add -A  # Add all files and commit them
git commit
git branch -D main  # Deletes the master branch
git branch -m main  # Rename the current branch to master
git push -f origin main  # Force push master branch to github
#git gc --aggressive --prune=all     # remove the old files
```
