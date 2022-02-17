## Documentação

https://devdocs.magento.com/guides/v2.4/extension-dev-guide/events-and-observers.html

## Exemplo de Observer

etc/events.xml
```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Event/etc/events.xsd">
    <event name="email_shipment_set_template_vars_before">
        <observer name="SetTrackingUrl" instance="Synapcom\TrackingOrder\Observer\ShipmentSender" />
    </event>
</config>
```

Observer/ShipmentSender.php
```php
<?php

namespace Synapcom\TrackingOrder\Observer;

use Magento\Framework\DataObject;
use Magento\Framework\Event\Observer;
use Magento\Framework\Event\ObserverInterface;

class ShipmentSender implements ObserverInterface
{
    public function __construct()
    {
        // Observer initialization code...
        // You can use dependency injection to get any class this observer may need.
    }

    public function execute(Observer $observer)
    {
        $transportObject = $observer->getData('transportObject');
        $transportObject->setData('a', 'a');
        $order = $transportObject->getOrder();
    }
}

```