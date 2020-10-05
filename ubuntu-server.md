# Ubuntu Server Configuration

## Ubuntu Server 13.10 now goes to sleep when closing laptop lid

Edit `/etc/systemd/logind.conf`

```bash
HandleLidSwitch=ignore
```

Then execute `sudo restart systemd-logind` or simply reboot.

## Some useful commands

```bash

# Copy SSH public key to a remote server
ssh-copy-id server1.example.com

# Copy another SSH key to a remote server
ssh-copy-id -i ~/keys/foo foo@server1.example.com

# Add a user to the www-data group. Re-login for permissions to take effect.
sudo usermod -a -G www-data foo

# Change ownership of files recursively
sudo chown -R foo:bar bootstrap/cache
sudo chown -R foo:bar storage/*

# Disk speed test
time dd if=/dev/zero of=iotest bs=64k count=16k conv=fdatasync

# Another disk speed test
time dd if=/dev/zero of=iotest oflag=direct bs=64k count=16000

# List directories by size
du -s ~/* |sort -nr

# Print sizes in human readable format (e.g., 1K 234M 2G):
du -sh ~/* |sort -hr

# Empty Trash Folder
rm -rf ~/.local/share/Trash/*

# List processes
ps -f
ps -ef

```

## Inxi

inxi shows system hardware, CPU, drivers, Xorg, Desktop, Kernel,
GCC version(s), Processes, RAM usage, and a wide variety of other useful information.

```bash

sudo apt-get install inxi

inxi -Fx

```

## Setting locale failed

My guess is you used ssh to connect to this older host from a newer desktop machine.
It's common for `/etc/ssh/sshd_config` to contain

    AcceptEnv LANG LC_*

```bash

# Edit the sshd_config by removing "AcceptEnv LANG LC_*", then restart ssh
# server:
sudo service ssh restart

# Test by running this command. There must be no output nor errors.
perl -e exit

```
