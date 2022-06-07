## Como criar uma Cron Job

Recurso: https://magefan.com/blog/create-custom-cron-job-in-magento-2

## Exemplo

`etc/crontab.xml`
```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="fcamara_b2e_cron_disable_expirated_coupon" instance="FCamara\B2E\Cron\DisableExpiratedCoupon" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

```
* * * * * command to be executed
| | | | |
| | | | +----- Day of week (0 - 7) (Sunday=0 or 7)
| | | +------- Month (1 - 12)
| | +--------- Day of month (1 - 31)
| +----------- Hour (0 - 23)
+------------- Minute (0 - 59)
``` 