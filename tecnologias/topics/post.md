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