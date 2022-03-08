## Exemplo

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Customer\Controller\Account\LoginPost">
        <plugin name="fcamara_after_execute" type="FCamara\OnestepCheckout\Plugin\Controller\Account\LoginPost"
                sortOrder="1" disabled="false"/>
    </type>
</config>
```

Classe PHP
```php
<?php

namespace FCamara\OnestepCheckout\Plugin\Controller\Account;

use Magento\Framework\App\RequestInterface;

class LoginPost
{
    /**
     * @var RequestInterface
     */
    protected RequestInterface $request;

    /**
     * @param RequestInterface $request
     */
    public function __construct(RequestInterface $request)
    {
        $this->request = $request;
    }

    /**
     * @return mixed
     */
    public function getPostReferer()
    {
        return $this->request->getPostValue('referer');
    }

    /**
     * @param \Magento\Customer\Controller\Account\LoginPost $subject
     * @param $result
     * @return mixed
     */
    public function afterExecute(\Magento\Customer\Controller\Account\LoginPost $subject, $result)
    {
        $result->setPath($this->getPostReferer());
        return $result;
    }
}
```