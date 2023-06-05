## Objeto Request (API Rest do Magento 2)

```php
<?php

namespace FCamara\ProductSubscription\Model\Api;

use Magento\Framework\Webapi\Rest\Request;

/**
 * @var Request
 */
protected Request $request;

public function __construct(Request $request)
{
    $this->request = $request;
}

$params = $this->request->getBodyParams();
}


```

## Objeto Request

```php
use Magento\Framework\App\RequestInterface;

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
```