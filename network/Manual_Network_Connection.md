# Make computer automatically connect to a network

Here are some examples of network configurations that can be added to your network interfaces (`sudo vim /etc/network/interfaces`)
You should adapt the names and values according to your network.

### Ethernet Static IP
```
auto [eth name]
iface [eth name] inet static
address 10.5.5.1
netmask 255.255.255.0
```

### DHCP Wi-FI
```
auto wlan0
iface wlan0 inet dhcp
wpa-essid mywifiname
wpa-psk mypass
```

### Static IP Wi-Fi
```
auto wlan0
iface wlan0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wpa-essid mywifiname
wpa-psk mypass
```
