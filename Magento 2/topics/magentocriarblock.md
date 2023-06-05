## Como criar um block

```php
<?php

namespace FCamara\MundiPagg\Block\Customer;

use Magento\Framework\View\Element\Template;
use Magento\Framework\View\Element\Template\Context;

class Transactions extends Template
{
    public function __construct(Context $context)
    {
        parent::__construct($context);
    }
}
```