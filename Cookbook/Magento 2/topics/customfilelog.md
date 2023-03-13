## 1. Criar Handler

`FCamara\B2E\Logger\Handler.php`

```php
<?php
namespace FCamara\B2E\Logger;

use Magento\Framework\Logger\Handler\Base as BaseHandler;
use Monolog\Logger;

class Handler extends BaseHandler
{
    /**
     * Logging level
     * @var int
     */
    protected $loggerType = Logger::INFO;

    /**
     * File name
     * @var string
     */
    protected $fileName = '/var/log/b2e_cron.log';
}
```

## 2. Criar virtualType e type

`FCamara\B2E\etc\di.xml`

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <!-- Logging -->
    <virtualType name="FCamara\B2E\Logger\Logger" type="Monolog\Logger">
        <arguments>
            <argument name="name" xsi:type="string">b2eLogger</argument>
            <argument name="handlers" xsi:type="array">
                <item name="system" xsi:type="object">FCamara\B2E\Logger\Handler</item>
            </argument>
        </arguments>
    </virtualType>
    <type name="FCamara\B2E\Cron\DisableExpiratedCoupon">
        <arguments>
            <argument name="logger" xsi:type="object">FCamara\B2E\Logger\Logger</argument>
        </arguments>
    </type>
</config>
```