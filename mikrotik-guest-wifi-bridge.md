### Created secured guest Wireless network

- Add wireless security profile
- Add wireless virtual interface

```
/interface wireless security-profiles
add authentication-types=wpa2-psk mode=dynamic-keys name=guest wpa2-pre-shared-key=password
/interface wireless
add disabled=no master-interface=wlan-lokiloki name=wlan-foo security-profile=guest ssid=foobar
```

Create bridge and add bridge ports

```
/interface bridge
add fast-forward=no name=foobar
/interface bridge port
add bridge=foobar interface=wlan-foo
```

Add IP address and IP address pool

```
/ip address
add address=10.1.21.1/24 interface=foobar network=10.1.21.0
/ip pool
add name=foobar ranges=10.1.21.2-10.1.21.254
```

Add DHCP server and network

```
/ip dhcp-server
add address-pool=foobar disabled=no interface=foobar name=foobar
/ip dhcp-server network
add address=10.1.21.0/24 dns-server=10.1.21.1 gateway=10.1.21.1
```

