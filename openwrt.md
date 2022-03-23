# opkg
```sh
opkg update
opkg install tcpdump
```
# procd
Restart
```
killall dnsmasq
/etc/init.d/dnsmasq start
```
Turn off completely
```
/etc/init.d/firewall disable
/etc/init.d/firewall stop
```
# dnsmasq
https://openwrt.org/ru/doc/howto/dhcp.dnsmasq
# wireshark
https://openwrt.org/docs/guide-user/firewall/misc/tcpdump_wireshark  
`ssh root@openwrt tcpdump -i eth0.2 -U -s0 -w - 'not port 22' | "C:\Program Files\Wireshark\Wireshark.exe" -k -i -`
