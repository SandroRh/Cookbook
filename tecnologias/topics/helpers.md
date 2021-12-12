# Helpers
Helpers são classes com funções de auxílio para uma determinada classe. Essa determinada classe delega para o helper a responsabilidades de certos métodos, chamamos isso de proxy methods.

## Como criar um Helper

Estrutura
- Helper
   - Product.php

Código
```php
class Product extends \Magento\Framework\Url\Helper\Data 
{

}
```

A utilização de helpers é feita via Dependency Injection (DY).