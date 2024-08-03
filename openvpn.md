# systemd service
`systemctl status openvpn-server@server`
# Show client list
`journalctl -xeu openvpn-server@server | grep "primary virtual IP for "`
