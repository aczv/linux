https://www.virtualbox.org/wiki/Linux_Downloads

# Debian-based Linux distributions

## Create a new file in /etc/apt/sources.list.d:

    sudo nano /etc/apt/sources.list.d/virtualbox.list

Add the following line:

    deb http://download.virtualbox.org/virtualbox/debian trusty contrib

According to your distribution, replace 'vivid' by 'utopic', 'trusty', 'raring', 'quantal',
'precise', 'lucid', 'jessie', 'wheezy', or 'squeeze'.

(Up to version 3.2 the packages were located in the non-free section. Starting with 
version 4.0 they are located in the contrib section.)

## The Oracle public key for apt-secure can be downloaded here:

    wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

## To install VirtualBox, do

    sudo apt-get update
    sudo apt-get install virtualbox-5.0

## Install dkms

Note: Ubuntu/Debian users might want to install the dkms package to ensure that the VirtualBox
host kernel modules (vboxdrv, vboxnetflt and vboxnetadp) are properly updated if the linux 
kernel version changes during the next apt-get upgrade. For Debian it is available in 
Lenny backports and in the normal repository for Squeeze and later. The dkms package 
can be installed through the Synaptic Package manager or through the following command:

    sudo apt-get install dkms

