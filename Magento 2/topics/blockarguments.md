## Como funciona

1. No arquivo XML, dentro do block
```xml
<arguments>
    <argument name="lastOrder" xsi:type="object">FCamara\Checkout\Model\LastOrder</argument>
    <argument name="teste" xsi:type="string">Olá mundo!</argument>
</arguments>
```
2. No template do block

```php
$block->getData('lastOrder'); # 1
$block->getTeste(); # 2
```