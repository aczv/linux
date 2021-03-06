# My Ubuntu 20.04 Desktop

## Install common tools

```bash
sudo apt-get install \
    curl git htop mc net-tools tree \
    openssh-server \
    cifs-utils smbclient ffmpeg
```

## Configure SSH client

Edit `/etc/ssh/ssh_config` and comment out SendEnv LANG LC_* line.

## Alt-TAB messed up

```bash
sudo apt-get install compizconfig-settings-manager
```

## Configure Git

```bash
git config --global user.email "andrius@cepaitis.eu"
git config --global user.name "Andrius Cepaitis"
```

## Ubuntu 20.04 won't boot on Lenovo T470 while in docking station

https://askubuntu.com/questions/1230122/20-04-wont-boot-on-lenovo-t470-while-in-docking-station

```bash
sudo nano /etc/default/grub
```

Replace line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" with:

    GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash"

```bash
sudo update-grub
```

## Install SublimeText

https://www.sublimetext.com/docs/3/linux_repositories.html#apt

```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update
sudo apt-get install sublime-text
```

### Preferences / Settings

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

### Install Packages:

- https://packagecontrol.io/packages/
- https://glennkimble.me/blog/eslint-for-vuejs-in-sublime-text-3/

Install packages from Command Palette (CTRL+SHIFT+P):

- Djaneiro
- ESLint Fix
- Package Control
- Pretty JSON
- Sass
- SideBarEnhancements
- SublimeLinter
- SublimeLinter-eslint
- Vue Syntax Highlight

Open up the command-palette (again) and type Preferences: SublimeLinter
Settings. We'll need to add this to the config on the right side.

```json

"linters": {
    "eslint": {
        "selector": "text.html.vue, source.js - meta.attribute-with-value"
    }
}

```

## Install Oh My Zsh

- https://github.com/ohmyzsh/ohmyzsh
- https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins

## Mount NAS disks

Edit `/etc/fstab`:

```
//192.168.24.34/y  /media/nas1_y  cifs  credentials=/root/.smbnas1,vers=3.0,iocharset=utf8,uid=1000,gid=1000,ro  0  0
//192.168.24.34/z  /media/nas1_z  cifs  credentials=/root/.smbnas1,vers=3.0,iocharset=utf8,uid=1000,gid=1000  0  0
```

Create mount points and map the disks now.

```bash
sudo mkdir -p /media/nas1_{y,z}
sudo mount -a
ls -l /media/nas1_y
```

## Install pyenv, then Poetry

- https://github.com/pyenv/pyenv#basic-github-checkout
- https://python-poetry.org/docs/#installation

```bash

rm -rf ~/.pyenv
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc

# Restart shell
exec "$SHELL"

# Install a Python version
pyenv install 3.8.6

# Set global Python version
pyenv global 3.8.6

# Check Python version
python --version

# Install Poetry
curl -O https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py
python get-poetry.py --no-modify-path --version 1.0.9
echo 'export PATH="$HOME/.poetry/bin:$PATH"' >> ~/.bashrc

# Restart shell
exec "$SHELL"

# Check Poetry version
poetry --version

```

## Install PostgreSQL

```bash
sudo apt-get install postgresql-12
```

## Install RabbitMQ

```bash
sudo apt install rabbitmq-server
sudo rabbitmq-plugins enable rabbitmq_management
```

## Install SmartGit

https://www.syntevo.com/smartgit/download/

```bash

sudo dpkg -i smartgit-20_1_5.deb
sudo apt --fix-broken install

```

## Install DBeaver

https://dbeaver.io/download/

```bash

sudo dpkg -i dbeaver-ce_7.2.2_amd64.deb
sudo apt --fix-broken install

```

## Install Node

- https://github.com/nvm-sh/nvm#install--update-script
- https://classic.yarnpkg.com/en/docs/install/#debian-stable
- https://cli.vuejs.org/guide/installation.html

```bash

# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.36.0/install.sh | bash

# Install Yarn
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn

# Install Vue CLI
npm install -g @vue/cli

```
