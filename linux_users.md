# User
Current user
```
id
```
See user info
```
cat /etc/passwd
```
User groups
```
groups <user>
```
# Group
Add group
```
sudo groupadd <grp>
```
Add existing user to a group
```
sudo usermod -aG <grp> <user>
```
# chmod
Add write permissions to file group
chmod -R g+rwx <file>
