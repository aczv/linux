# Prepare my new Linux for work.

## Install Common Tools

```bash
sudo apt install curl git htop mc net-tools

# Install SSH server in Ubuntu
sudo apt-get install openssh-server

# Install CIFS utilities
sudo apt-get install cifs-utils smbclient
```

## Configure SSH client

Edit `/etc/ssh/ssh_config` and comment out SendEnv LANG LC_* line.


## Configure Git

```bash
git config --global user.email "andrius@cepaitis.eu"
git config --global user.name "Andrius Cepaitis"
```

## Install SublimeText

https://www.sublimetext.com/docs/3/linux_repositories.html#apt

```json
{
    "font_size": 14,
    "rulers": [80, 100, 120],
    "tab_size": 4,
    "translate_tabs_to_spaces": true,
    "line_padding_top": 2,
    "line_padding_bottom": 2,
    "trim_trailing_white_space_on_save": true,
    "ensure_newline_at_eof_on_save": true,
    "save_on_focus_lost": true,
    "ignored_packages":
    [
        "Vintage"
    ]
}
```

### Sublime Packages

- MarkdownEditing
- Vue Syntax Highlight

## Install Oh My Zsh

https://github.com/robbyrussell/oh-my-zsh

Some plugins:

git docker osx z

More plugins:

https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins-Overview

## Install TLP

Advanced power management for Linux.

http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#installation

### T450s

```bash
sudo apt-get update
sudo apt-get install tlp acpi-call-dkms
```

### X60

```bash
sudo apt-get update
sudo apt-get install tlp tp-smapi-dkms
```

## Ubuntu 20.04 won't boot on Lenovo T470 while in docking station

https://askubuntu.com/questions/1230122/20-04-wont-boot-on-lenovo-t470-while-in-docking-station

I have the same problem. My L450 does not boot while docked (ThinkPad Pro Dock 40A1), but it boots with disconnected additional monitor. All has worked while i disabled boot splash screen (GRUB_CMDLINE_LINUX_DEFAULT="nosplash" in /etc/default/grub).

I can confirm that replacing line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" with GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash" in /etc/default/grub fixed the issue. Also after editing need to execute update-grub.
