# Developer Tools

GUI and command line tools for developer.

## Install Oracle (Sun) Java 8

Follow instructions to [Install Oracle Java 8 in Ubuntu][oracle]

    sudo add-apt-repository ppa:webupd8team/java
    sudo apt-get update
    sudo apt-get install oracle-java8-installer

### Check Java version

    java -version
    javac -version

## Install SmartGit

[Download][smartgit-download] SmartGit zip from the web

### Extract files from zip

Extract zip files and move the new directory from `~/Downloads` to `~/bin`

    tar xf smart*7.1*
    mv ~/Downloads/smartgit ~/bin

### Create Unity Launcher menu item:

    ./add-menuitem.sh

## Install PhpStorm EAP

Download [PhpStorm Early Access Program][PhpStorm EAP] from JetBrains.

### Extract zip

Extract files from zip to `~/bin` directory

$$$ TEST IT

    tar xfz PhpStorm-*.tar.gz
    mv PhpStorm-141.1619 ~/bin

Start PhpStorm

    cd ~/bin/PhpStorm-*/bin
    ./PhpStorm.sh

### Create Launcher icon

$$$ TODO patikrinti is kurio meniu 'create shortcut'

### Laravel IDE Helper

Installation [instructions][laravel-ide-helper] on GitHub. 

### Inotify Watches Limit

To prevent [this situation][inotify-limit] it is recommended to increase the watches limit (to, say, 512K).
You can do it by adding following line to the `/etc/sysctl.conf` file:

    fs.inotify.max_user_watches = 524288

Then run this command to apply the change:

    sudo sysctl -p

And don't forget to restart your IDE.

## Install Xdebug

    sudo apt-get install php5-xdebug

### Change recursion nesting level

To change recursion nesting level, edit:

    sudo nano /etc/php5/fpm/conf.d/20-xdebug.ini

Add line:

    xdebug.max_nesting_level=200



[oracle]: http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html
[smartgit-download]: http://www.syntevo.com/smartgit/download
[PhpStorm EAP]: https://confluence.jetbrains.com/display/PhpStorm/PhpStorm+Early+Access+Program
[laravel-ide-helper]: https://github.com/barryvdh/laravel-ide-helper
[inotify-limit]: https://confluence.jetbrains.com/display/IDEADEV/Inotify+Watches+Limit
[ffmpeg-compile]: http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu

