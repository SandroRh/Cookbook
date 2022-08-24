# Desenvolvimento do teste
Métodos necessários para todos os testes unitários:

1. testInstance()
2. setUp()

## Exemplo real

```php
<?php

namespace Infracommerce\CustomerEmail\Test\Unit\Controller\Account;

use Infracommerce\CustomerEmail\Controller\Account\EmailConfirm;
use Magento\Customer\Api\CustomerRepositoryInterface;
use Magento\Customer\Api\Data\CustomerInterface;
use Magento\Framework\Api\AttributeInterface;
use Magento\Framework\App\RequestInterface;
use PHPUnit\Framework\TestCase;
use Magento\Framework\Message\ManagerInterface;

class EmailConfirmTest extends TestCase
{
    /**
     * @var EmailConfirm
     */
    private $object;

    public function testInstance(): void
    {
        $this->assertInstanceOf(EmailConfirm::class, $this->object);
    }

    public function testExecute(): void
    {
        $this->request
            ->expects($this->at(0))
            ->method('getParam')
            ->with('id', false)
            ->willReturn($customerId = 1);

        $this->request
            ->expects($this->at(1))
            ->method('getParam')
            ->with('key', false)
            ->willReturn($key = "1234");

        $this->customerRepository
            ->expects($this->once())
            ->method('getById')
            ->with($customerId)
            ->willReturn($this->custo
            ->with($customerId)
            ->willReturn($this->customer);

        $this->customer
            ->expects($this->once())
            ->method('getCustomAttribute')
            ->with("temp_email")
            ->willReturn($this->attributeInterface);

        $result = $this->object->execute();
    }

    protected function setUp(): void
    {
        $this->messageManager = $this->createMock(ManagerInterface::class);
        $this->request = $this->createMock(RequestInterface::class);
        $this->customerRepository = $this->createMock(CustomerRepositoryInterface::class);
        $this->resultFactory = $this->getMockBuilder('\Magento\Framework\Controller\ResultFactory')
            ->disableOriginalConstructor()
            ->setMethods(['create'])
            ->getMock();
        $this->customer = $this->createMock(CustomerInterface::class);

        $this->resultFactory->method('create')
            ->willReturn($this->createMock(\Magento\Framework\Controller\Result\Redirect::class));

        $this->attributeInterface = $this->createMock(AttributeInterface::class);

        $this->object = new EmailConfirm(
            $this->messageManager,
            $this->request,
            $this->customerRepository,
            $this->resultFactory
        );
    }
}
```