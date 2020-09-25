## Users

### Copy SSH public key to a remote server

```
ssh-copy-id server1.example.com
```

### Copy another SSH key to a remote server

```
ssh-copy-id -i ~/keys/foo foo@server1.example.com
```

### Install SSH public key manually

https://www.digitalocean.com/community/tutorials/how-to-create-ssh-keys-with-putty-to-connect-to-a-vps

If your SSH folder does not yet exist, create it:

```
mkdir ~/.ssh
chmod 0700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 0644 ~/.ssh/authorized_keys
```

Paste the SSH public key into your `~/.ssh/authorized_keys` file (see Installing and Using the Vim Text Editor on an Cloud Server):

```
sudo vim ~/.ssh/authorized_keys
```

Tap the i key on your keyboard & right-click your mouse to paste.
To save, tap the following keys on your keyboard (in this order): Esc, :, w, q, Enter.

### Add a user to the www-data group

```
sudo usermod -a -G www-data foo
```

Will have to re-login for permissions to take effect.

### Change ownership of files recursively

```
sudo chown -R foo:bar bootstrap/cache
sudo chown -R foo:bar storage/*
```

## Performance tests

### Disk speed test

```
dd if=/dev/zero of=iotest bs=64k count=16k conv=fdatasync
```

### Inxi

```
inxi -Fx
```

inxi shows system hardware, CPU, drivers, Xorg, Desktop, Kernel,
GCC version(s), Processes, RAM usage, and a wide variety of other useful information.
Install inxi:

```
apt-get install inxi
```

### Slow disk TEST

```
time dd if=/dev/zero of=/tmp/test oflag=direct bs=64k count=16000
```

## List directories by size

```
du -s ~/* |sort -nr
```

Print sizes in human readable format (e.g., 1K 234M 2G):

```
du -sh ~/* |sort -hr
```

## Empty Trash Folder

```
rm -rf ~/.local/share/Trash/*
```

## List processes

```
ps -f
ps -ef
```
