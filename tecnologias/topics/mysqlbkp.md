## Fonte

https://support.hostway.com/hc/en-us/articles/360000220190-How-to-backup-and-restore-MySQL-databases-on-Linux

## Como criar backup

```php
sudo mysqldump --no-tablespaces -u magento -p magentosales > dump_file.sql
```

## Como executar backup
```php
mysql -u magento -p magentosales < dump_file.sql
```