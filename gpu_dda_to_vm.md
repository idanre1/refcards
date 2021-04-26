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

# download driver
https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/
https://us.download.nvidia.com/XFree86/Linux-x86_64/460.73.01/NVIDIA-Linux-x86_64-460.73.01.run
####sudo apt install nvidia-driver-460 xterm
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/nvidia-driver-465_465.19.01-0ubuntu1_amd64.deb
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub

# setup nat switch
https://tewarid.github.io/2019/06/26/port-forwarding-in-hyper-v.html
New-VMSwitch -SwitchName "NATSwitch" -SwitchType Internal
New-NetIPAddress -IPAddress 192.168.10.1 -PrefixLength 24 -InterfaceAlias "vEthernet (NATSwitch)"
New-NetNAT -Name "NATNetwork" -InternalIPInterfaceAddressPrefix 192.168.10.0/24
Add-NetNatStaticMapping -ExternalIPAddress "0.0.0.0/24" -ExternalPort 22 -Protocol TCP -InternalIPAddress "192.168.10.2" -InternalPort 22 -NatName NATNetwork

# on vm static ip
sunet: 192.168.10.0/24
address: 192.168.10.2
gateway: 192.168.10.1
name servers: 10.50.50.50, 10.50.10.50
