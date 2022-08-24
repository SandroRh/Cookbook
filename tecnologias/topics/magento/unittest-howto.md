## Como mockar uma factory class?

```php
$this->resultFactory = $this->getMockBuilder('\Magento\Framework\Controller\ResultFactory')
            ->disableOriginalConstructor()
            ->setMethods(['create'])
            ->getMock();
            
$this->resultFactory->method('create')
            ->willReturn($this->createMock(\Magento\Framework\Controller\Result\Redirect::class));
```

## Como simular a execução de um método?

```php
$this->request
            ->expects($this->at(0))
            ->method('getParam')
            ->with('id', false)
            ->willReturn($customerId = 1);
```

## Como instanciar um objeto com o ObjectManagerHelper

```php
use Magento\Framework\TestFramework\Unit\Helper\ObjectManager;

$helper = new ObjectManager($this);

$this->view = $helper->getObject(
            View::class,
            ['productTypeConfig' => $this->productTypeConfig, 'registry' => $this->registryMock]
        );
```