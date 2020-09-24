

## Install Poetry on Ubuntu 20.04

https://python-poetry.org/docs/#installation

```bash
# Install pip3
sudo apt-get install python3-pip python3-venv

# Install curl
sudo apt install curl

# Install Poetry (notice python3 at the end)
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3
```

## Install Sublime Text 3

https://www.sublimetext.com/docs/3/linux_repositories.html

```bash

wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update
sudo apt-get install sublime-text

```

