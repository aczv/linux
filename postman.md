## Postman

https://www.getpostman.com/docs/v6/postman/launching_postman/installation_and_updates

https://blog.bluematador.com/posts/postman-how-to-install-on-ubuntu-1604

#### Install Postman on Ubuntu 16.04

Postman recommends installing its native app, but there wasn’t any documentation for installing it on Ubuntu — just a download link. So, in order to make it easier for fellow Ubuntu users to start with Postman, here are some quick commands to get set up!

```bash
wget https://dl.pstmn.io/download/latest/linux64 -O postman.tar.gz
sudo tar -xzf postman.tar.gz -C /opt
rm postman.tar.gz
sudo ln -s /opt/Postman/Postman /usr/bin/postman
```

#### Postman Unity launcher link

As a bonus, here’s a command to create an Unity desktop file for your launcher. After you create the file, logout and then log back in, you’ll be able to search for “Postman” in your Unity launcher to start up the Postman app.

```bash
cat > ~/.local/share/applications/postman.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=postman
Icon=/opt/Postman/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
EOL
```
