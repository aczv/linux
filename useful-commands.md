## Users

### Copy SSH public key to a remote server

```
ssh-copy-id server1.example.com
```

### Copy another SSH key to a remote server

```
ssh-copy-id -i ~/keys/foo foo@server1.example.com
```

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

