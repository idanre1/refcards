https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/deploying-graphics-devices-using-dda
https://searchvirtualdesktop.techtarget.com/tip/Running-GPU-passthrough-for-a-virtual-desktop-with-Hyper-V?amp=1

open power shell
Enter-PSSession Server01

# guide from dell
https://www.dell.com/support/kbdoc/en-il/000106925/how-to-configure-a-gpu-using-discrete-device-assignment-dda-on-ubuntu-guest-operating-system

# hyper-v
install gen2 ubuntu VM named "Ubuntu"

# on host
device-manager->goto display driver
location path: copy the PCIE details: "PCIROOT(64)#PCI(0000)#PCI(0000)"
then disable device

Set-VM -Name Ubuntu -AutomaticStopAction TurnOff
Set-VM -VMName Ubuntu -GuestControlledCacheTypes $true
Set-VM -VMName Ubuntu -LowMemoryMappedIoSpace 128Mb
Set-VM -VMName Ubuntu -HighMemoryMappedIoSpace 18000Mb

Dismount-VMHostAssignableDevice -force -LocationPath "PCIROOT(64)#PCI(0000)#PCI(0000)"
Add-VMAssignableDevice -VMName Ubuntu -LocationPath "PCIROOT(64)#PCI(0000)#PCI(0000)"

# on VM
$ lspci
$ sudo lshw -C Display

## remove display driver
- Create a file at /etc/modprobe.d/blacklist-nouveau.conf
$ sudo nano /etc/modprobe.d/blacklist-nouveau.conf

- Add the content to the created file then save file
blacklist nouveau
options nouveau modeset=0

- Regenerate the kernel initramfs then reboot
$ sudo update-initramfs -u
$ reboot

# download driver
https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/
https://us.download.nvidia.com/XFree86/Linux-x86_64/460.73.01/NVIDIA-Linux-x86_64-460.73.01.run
sudo apt install nvidia-driver-460
