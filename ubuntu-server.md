# Ubuntu Server Configuration

## Ubuntu Server 13.10 now goes to sleep when closing laptop lid

I recently upgraded to the latest version (13.10). I have it running on an old laptop. Since the upgrade, whenever I close the laptop lid, it goes to sleep mode. I realized that Ubuntu 13.10 uses `systemd-logind` and it handles the lid close event. To disable entering the sleep mode edit the

```
sudo nano /etc/systemd/logind.conf
```

file and uncomment/modify/add the line:

```
HandleLidSwitch=ignore
```

Then execute `sudo restart systemd-logind` or simply reboot.

## Set default editor

```
export EDITOR=nano
```

## Set Static IP address

Let’s open up the `/etc/network/interfaces` file. I'm going to use vi, but you can choose a different editor

    sudo vi /etc/network/interfaces

For the primary interface, which is usually eth0, you will see these lines:

    auto eth0
    iface eth0 inet dhcp

As you can see, it’s using DHCP right now. We are going to change dhcp to static, and then there are a number of options that should be added below it. Obviously you’d customize this to your network.

    auto eth0
    iface eth0 inet static
            address 192.168.1.100
            netmask 255.255.255.0
            network 192.168.1.0
            broadcast 192.168.1.255
            gateway 192.168.1.1

Now we’ll need to add in the DNS settings by editing the `resolv.conf` file:

    sudo vi /etc/resolv.conf

On the line ‘name server xxx.xxx.xxx.xxx’ replace the x with the IP of your name server. (You can do `ifconfig /all` to find out what they are)

You need to also remove the dhcp client for this to stick (thanks to Peter for noticing). You might need to remove dhcp-client3 instead.

    sudo apt-get remove dhcp-client

Now we’ll just need to restart the networking components:

    sudo /etc/init.d/networking restart

Ping www.google.com. If you get a response, name resolution is working (unless of course if google is in your hosts file).

