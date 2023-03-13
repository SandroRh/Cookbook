## O que é

https://devdocs.magento.com/guides/v2.4/extension-dev-guide/factories.html

Factories are service classes that instantiate non-injectable classes, that is, models that represent a database entity. They create a layer of abstraction between the ObjectManager and business code.

`Model + Factory`.

Exemplo: $orderFactory

Esse objeto é armazenado em `var/generation/<vendor_name>/<module_name>/Model/ClassFactory.php`.

## Exemplo

```php
<?php
namespace Mageplaza\HelloWorld\Controller\Index;

class Index extends \Magento\Framework\App\Action\Action
{
	protected $_pageFactory;

	protected $_postFactory;

	public function __construct(
		\Magento\Framework\App\Action\Context $context,
		\Magento\Framework\View\Result\PageFactory $pageFactory,
		\Mageplaza\HelloWorld\Model\PostFactory $postFactory
		)
	{
		$this->_pageFactory = $pageFactory;
		$this->_postFactory = $postFactory;
		return parent::__construct($context);
	}

	public function execute()
	{
		$post = $this->_postFactory->create();
		$collection = $post->getCollection();
		foreach($collection as $item){
			echo "<pre>";
			print_r($item->getData());
			echo "</pre>";
		}
		exit();
		return $this->_pageFactory->create();
	}
}
```