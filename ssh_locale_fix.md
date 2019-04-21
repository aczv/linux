

## Setting locale failed

My guess is you used ssh to connect to this older host from a newer desktop machine.
It's common for `/etc/ssh/sshd_config` to contain

    AcceptEnv LANG LC_*

Edit the sshd_config by removing "AcceptEnv LANG LC_*", then restart ssh server:

    sudo service ssh restart

Test by running this command. There must be output nor errors.

    perl -e exit

