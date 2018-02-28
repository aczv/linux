### Created secured guest Wireless network

- Add wireless security profile
- Add wireless virtual interface

```
/interface wireless security-profiles
add authentication-types=wpa2-psk mode=dynamic-keys name=guest wpa2-pre-shared-key=password
/interface wireless
add disabled=no master-interface=wlan-lokiloki name=wlan-guest security-profile=guest ssid=guest
```

- Create bridge with vlan-filtering=yes
- Add necessary bridge ports

```
/interface bridge
add fast-forward=no name=guest pvid=444 vlan-filtering=yes
/interface bridge port
add bridge=guest interface=wlan-guest pvid=444
```

Add IP address and IP address pool

```
/ip address
add address=10.0.21.1/24 interface=guest network=10.0.21.0
/ip pool
add name=guest ranges=10.0.21.2-10.0.21.254
```

Add DHCP server and network

```
/ip dhcp-server
add address-pool=guest disabled=no interface=guest name=guest
/ip dhcp-server network
add address=10.0.21.0/24 dns-server=10.0.21.1 gateway=10.0.21.1
```

