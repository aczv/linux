## List all cron jobs for all users

You would have to run this as root, but:

```
for user in $(cut -f1 -d: /etc/passwd); do crontab -u $user -l; done
```

will loop over each user name listing out their crontab. The crontabs are owned by the respective
users so you won't be able to see another user's crontab w/o being them or root.

If you want to know, which user does a crontab belong to insert - echo $ user

```
for user in $(cut -f1 -d: /etc/passwd); do echo $user; crontab -u $user -l; done
```

Source:

- http://stackoverflow.com/questions/134906/how-do-i-list-all-cron-jobs-for-all-users

