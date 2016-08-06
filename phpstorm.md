# PhpStorm EAP

Installation and configuration of *PhpStorm Early Access Program*

Download [PhpStorm Early Access Program][PhpStorm EAP] from JetBrains,
select `Linux` download option.

[PhpStorm EAP]: https://confluence.jetbrains.com/display/PhpStorm/PhpStorm+Early+Access+Program

Extract the downloaded zip file into `/usr/local/bin/` directory, e.g.:

```
cd ~/Downloads
ll PhpStorm*
sudo tar xzvf PhpStorm-EAP-162.1447.5.tar.gz -C /usr/local/bin/
```

Start PhpStorm from command line:

```
/usr/local/bin/PhpStorm-162.1447.5/bin/phpstorm.sh
```

When asked to import settings, choose 'I do not have previous version of PhpStorm'.

In the License Activation window choose Evaluate for free.

In PhpStorm Initial Configuration window leave 'create desktop entry' checkbox, and press OK.

Now close the PhpStorm and restart form the desktop launcher (press the `Windows` key,
type 'php', and then click on the PhpStorm icon).

To import previously saved settings, open File | Import Settings, and choose a `settings.jar`
file that you have handy on disk.

## Inotify Watches Limit

[inotify-limit]: https://confluence.jetbrains.com/display/IDEADEV/Inotify+Watches+Limit

To prevent [this situation][inotify-limit] it is recommended to increase the watches limit (to, say, 512K).
You can do it by adding following line to the `/etc/sysctl.conf` file:

```
fs.inotify.max_user_watches = 524288
```

Then run this command to apply the change:

```
sudo sysctl -p
```

And don't forget to restart your IDE.

## Install Xdebug

```
sudo apt-get install php5-xdebug
```

To change recursion nesting level, edit:

```
sudo nano /etc/php5/fpm/conf.d/20-xdebug.ini
```

and add the line:

```
xdebug.max_nesting_level=200
```

## Laravel IDE Helper

Installation [instructions][laravel-ide-helper] on GitHub.

[laravel-ide-helper]: https://github.com/barryvdh/laravel-ide-helper

