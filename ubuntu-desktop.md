## Ubuntu Desktop new installation

Edit /etc/ssh/ssh_config and comment out SendEnv LANG LC_* line.

## Ubuntu 20.04 won't boot on Lenovo T470 while in docking station

https://askubuntu.com/questions/1230122/20-04-wont-boot-on-lenovo-t470-while-in-docking-station

I have the same problem. My L450 does not boot while docked (ThinkPad Pro Dock 40A1), but it boots with disconnected additional monitor. All has worked while i disabled boot splash screen (GRUB_CMDLINE_LINUX_DEFAULT="nosplash" in /etc/default/grub).

I can confirm that replacing line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" with GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash" in /etc/default/grub fixed the issue. Also after editing need to execute update-grub. 
