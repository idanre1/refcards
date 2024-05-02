# UAC
Add remote admin to UAC  
https://superuser.com/questions/1293410/how-to-extend-default-choices-in-user-account-control-pop-up  
You can try typing `net localgroup Administrators User /add` into a command prompt with admin rights.  
Replace User with the user you would like to add to the UAC list.
