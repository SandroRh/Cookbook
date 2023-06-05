```php
namespace Company\Module\Controller\Index;
use Magento\Framework\Controller\ResultFactory; 

class Actionname name extends \Magento\Framework\App\Action\Action
{      
    private ResultFactory $resultFactory;

    public function __construct(ResultFactory $resultFactory) 
    {
        $this->resultFactory = $resultFactory;
    }

    public function execute()
    {
        $resultRedirect = $this->resultFactory->create(ResultFactory::TYPE_REDIRECT);

        // Your code

        $resultRedirect->setRefererUrl();
        return $resultRedirect;
    }
}
```