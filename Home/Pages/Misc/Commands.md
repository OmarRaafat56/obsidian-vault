[[Miscellaneous]]


Sudo nmcli connection modify "YOUR_WIFI" ipv6.method ignore

sudo nmcli connection modify "YOUR_WIFI" 802-11-wireless.mac-address-randomization never

nmcli device disconnect wlo1
nmcli device connect wlo1

journalctl -b | grep dhcp#### 
