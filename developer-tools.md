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



[oracle]: http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html
[smartgit-download]: http://www.syntevo.com/smartgit/download


