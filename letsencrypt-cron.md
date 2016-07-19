## Let's Encrypt - Set Up Auto Renewal

Let’s Encrypt certificates are valid for 90 days, but it’s recommended that you renew the
certificates every 60 days to allow a margin of error. At the time of this writing,
automatic renewal is still not available as a feature of the client itself, but
you can manually renew your certificates by running the Let’s Encrypt client
with the renew option.

To trigger the renewal process for all installed domains, run this command:

```
/opt/letsencrypt/letsencrypt-auto renew
```

Because we recently installed the certificate, the command will only check for the expiration
date and print a message informing that the certificate is not due to renewal yet. The output
should look similar to this:

```
Checking for new version...
Requesting root privileges to run letsencrypt...
   /root/.local/share/letsencrypt/bin/letsencrypt renew
Processing /etc/letsencrypt/renewal/example.com.conf

The following certs are not due for renewal yet:
  /etc/letsencrypt/live/example.com/fullchain.pem (skipped)
No renewals were attempted.
```

Notice that if you created a bundled certificate with multiple domains, only the base domain
name will be shown in the output, but the renewal should be valid for all domains included
in this certificate.

A practical way to ensure your certificates won’t get outdated is to create a cron job that
will periodically execute the automatic renewal command for you. Since the renewal first
checks for the expiration date and only executes the renewal if the certificate is less
than 30 days away from expiration, it is safe to create a cron job that runs every week
or even every day, for instance.

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

