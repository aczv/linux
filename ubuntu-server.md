### Ubuntu Server 13.10 now goes to sleep when closing laptop lid

I recently upgraded to the latest version (13.10). I have it running on an old laptop. Since the upgrade, whenever I close the laptop lid, it goes to sleep mode.

I've had the same problem and after a lot of reading, I realized that Ubuntu 13.10 uses systemd-logind and it handles the lid close event. To disable entering the sleep mode edit the

```
sudo nano /etc/systemd/logind.conf
```

file and uncomment/modify/add the line:

```
HandleLidSwitch=ignore
```

Then execute sudo restart systemd-logind or simply reboot.

### Set default editor

```
export EDITOR=nano
```
