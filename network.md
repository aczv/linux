## Network trouble

https://ubuntu.com/server/docs/network-configuration

```bash
sudo ip addr add 191.168.24.222/24 dev enp0s25

ip link set dev enp0s25 up
ip link set dev enp0s25 down

```
