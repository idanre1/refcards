# How to manage swap on azure machine
https://docs.microsoft.com/en-us/troubleshoot/azure/virtual-machines/oom-swap-file-linux-vm
# Query space
df -h /mnt  
xx is amount of GB*1024  
# How to setup swap:
`sudo vim /etc/waagent.conf`  
ResourceDisk.Format=y  
ResourceDisk.EnableSwap=y  
ResourceDisk.SwapSizeMB=xx  
# Example
%> df -h /mnt  
Filesystem      Size  Used Avail Use% Mounted on  
/dev/sdb1       3.9G   16M  3.7G   1% /mnt
## MB calc:
3.7*1024=3,788.8  
ResourceDisk.SwapSizeMB=3770
## Post reboot affect:
%> df /mnt  
Filesystem     1K-blocks    Used Available Use% Mounted on  
/dev/sdb1        4060864 3876864         0 100% /mnt  
