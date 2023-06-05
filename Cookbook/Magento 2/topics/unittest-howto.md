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

// Dentro de [] ficam os atributos da classe
$this->view = $helper->getObject(
            View::class,
            ['productTypeConfig' => $this->productTypeConfig, 'registry' => $this->registryMock]
        );
```

Nota: Dentro do array de getObject, podemos inserir qualquer atributo/variável que a classe que está sendo testada utilizará como parâmetro, exemplo:

```php
$this->object = $helper->getObject(
    AnalyticsTag::class,
    [
        '_category' => $this->_category
    ]
);
```

Quando a classe utilizar o $this->_category, o category a ser utilizado será o nosso mock.