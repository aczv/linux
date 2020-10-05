# Ubuntu Server Configuration

## Ubuntu Server 13.10 now goes to sleep when closing laptop lid

Edit `/etc/systemd/logind.conf`

```bash
HandleLidSwitch=ignore
```

Then execute `sudo restart systemd-logind` or simply reboot.
