# systemd service
`systemctl status openvpn-server@server`
# Show client list
`journalctl -xeu openvpn-server@server | grep "primary virtual IP for "`
# upgrade openvpn
`sudo apt update; sudo apt upgrade`  
Then reboot the system
# official install file with private repo
`https://packages.openvpn.net/as/install.sh`
