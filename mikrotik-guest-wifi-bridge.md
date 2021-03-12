## Created secured guest Wireless network

```bash
# Add wireless security profile
/interface wireless security-profiles
add authentication-types=wpa2-psk mode=dynamic-keys name=guest wpa2-pre-shared-key=password

# Add wireless virtual interface
/interface wireless
add disabled=no master-interface=wlan-lokiloki name=wlan-foo security-profile=guest ssid=foobar

# Create bridge
/interface bridge
add fast-forward=no name=foobar

# Add bridge port
/interface bridge port
add bridge=foobar interface=wlan-foo

# Add IP address
/ip address
add address=10.1.21.1/24 interface=foobar network=10.1.21.0

# Add address pool
/ip pool
add name=foobar ranges=10.1.21.2-10.1.21.254

# Add DHCP server
/ip dhcp-server
add address-pool=foobar disabled=no interface=foobar name=foobar

# Add network
/ip dhcp-server network
add address=10.1.21.0/24 dns-server=10.1.21.1 gateway=10.1.21.1
```

## Create Management Network (LAN)

```bash
# Create bridge
/interface bridge

# Add network
/ip dhcp-server network

# Add IP address
/ip address

# Add address pool
/ip pool

# Add DHCP server
/ip dhcp-server

# Add Firewall Filter Rule (bridge -> WAN)
/xxx

# Make winbox/www/ssh services Available From new LAN
/ip service
# set www address=192.168.21.0/24,192.168.22.0/24,192.168.24.0/24,10.0.21.0/28
# set winbox address=192.168.21.0/24,192.168.24.0/24,10.0.21.0/24

# Add input chain rule
/ip firewall filter
add action=accept chain=input in-interface=bridge-lan-10 place-before=[find chain =input comment ="drop all"]

# Add bridge port
/interface bridge port
add bridge=foobar interface=wlan-foo

```
