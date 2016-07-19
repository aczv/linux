## Let's Encrypt - Set Up Auto Renewal

Let’s Encrypt certificates are valid for 90 days, but it’s recommended that you renew the
certificates every 60 days to allow a margin of error.
Let's edit the crontab to create a new job that will run the renewal command every week.
To edit the crontab for the root user, run:

```
sudo crontab -e
```

Add the following lines:

```
30 2 * * 1 /opt/letsencrypt/letsencrypt-auto renew >> /var/log/letsencrypt-renew.log
40 2 * * 1 /etc/init.d/nginx reload
```

Save and exit. This will create a new cron job that will execute the letsencrypt-auto renew
command every Monday at 2:30 am, and reload Nginx at 2:40am (so the renewed certificate will be used).
The output produced by the command will be piped to a log file located at /var/log/letsencrypt-renewal.log.

Source:

- https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-14-04

