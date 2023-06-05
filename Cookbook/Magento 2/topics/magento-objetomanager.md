## Como usar

```php
<?php 
    $objectManager = \Magento\Framework\App\ObjectManager::getInstance();

<?php
    $objectManager = \Magento\Framework\App\ObjectManager::getInstance();
    /* Create a new product object */
    $product = $objectManager->create(\Magento\Catalog\Model\Product::class);
    /* Get a request object singleton */
    $request = $objectManager->get(\Magento\Framework\App\RequestInterface::class);    
```