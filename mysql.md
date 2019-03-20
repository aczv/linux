
### Dump the database

```bash
mysqldump -uusename -ppassword dbname >dbname.sql
```

### Restore the database

```bash
mysql -u root -p dbname < dumpfile.sql
```
