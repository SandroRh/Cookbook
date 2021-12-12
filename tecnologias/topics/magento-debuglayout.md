Fonte: https://www.rakeshjesadiya.com/list-of-layout-xml-for-a-current-page-magento-2/

```php
$objectManager = \Magento\Framework\App\ObjectManager::getInstance();
$xmlLayout = $objectManager->get(\Magento\Framework\App\View::class);
var_dump($xmlLayout->getLayout()->getUpdate()->getHandles());
```

Adicionar o código acima no final do index.php
