# Docs
https://docs.microsoft.com/en-us/azure/virtual-machines/linux/attach-disk-portal
# Find sdc
lsblk -o NAME,HCTL,SIZE,MOUNTPOINT | grep -i "sd"
# Format
sudo parted /dev/sdc --script mklabel gpt mkpart xfspart xfs 0% 100%
sudo mkfs.xfs /dev/sdc1
sudo partprobe /dev/sdc1
# mnt
sudo mkdir /datadrive
# fstab
sudo blkid
/dev/sda1: LABEL="cloudimg-rootfs" UUID="11111111-1b1b-1c1c-1d1d-1e1e1e1e1e1e" TYPE="ext4" PARTUUID="1a1b1c1d-11aa-1234-1a1a1a1a1a1a"
/dev/sda15: LABEL="UEFI" UUID="BCD7-96A6" TYPE="vfat" PARTUUID="1e1g1cg1h-11aa-1234-1u1u1a1a1u1u"
/dev/sdb1: UUID="22222222-2b2b-2c2c-2d2d-2e2e2e2e2e2e" TYPE="ext4" TYPE="ext4" PARTUUID="1a2b3c4d-01"
/dev/sda14: PARTUUID="2e2g2cg2h-11aa-1234-1u1u1a1a1u1u"
/dev/sdc1: UUID="33333333-3b3b-3c3c-3d3d-3e3e3e3e3e3e" TYPE="xfs" PARTLABEL="xfspart" PARTUUID="c1c2c3c4-1234-cdef-asdf3456ghjk"

then:
sudo nano /etc/fstab
UUID=33333333-3b3b-3c3c-3d3d-3e3e3e3e3e3e   /datadrive   xfs   defaults,nofail   1   2

then: reboot

# verify
lsblk -o NAME,HCTL,SIZE,MOUNTPOINT | grep -i "sd"
sda     1:0:1:0     320G
└─sda1              320G /mnt
sdb     3:0:0:0     128G
└─sdb1              128G /datadrive
sdc     0:0:0:0      30G
├─sdc1             29.9G /
├─sdc14               4M
└─sdc15             106M /boot/efi

