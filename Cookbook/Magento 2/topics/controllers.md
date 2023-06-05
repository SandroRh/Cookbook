## Fonte

https://www.mageplaza.com/magento-2-module-development/how-to-create-controllers-magento-2.html

## O que são controllers

Controllers são responsáveis por receber requisições, processar requisições e renderizar páginas.

Controllers rodam obrigatóriamente o método execute();

Existem dois tipos de controllers: frontend e backend. A diferença é que o controller backend precisa checar a permissão, que vem através do form key.

## Como um controller funciona?

`http://example.com/route_name/controller/action`

Onde:

`route_name:` unique_name (frontName) que vem de routes.xml.

`controller:` Nome da pasta dentro de Controller.

`action:` Classe com método execute responsável por processar a requisição.

Todas as requisições passam por `Magento\Framework\App\FrontController`.

## Como criar um Controller?

```
Step 1: Create routes.xml file
Step 2: Create controller file
Step 3: Create controller Layout file
Step 4: Create controller Block file
Step 5: Create controller template file
Step 6: Flush Magento cache
Step 7: Run a test new controller
```

## Step 1: Create routes.xml file (in frontend or admin).

File: app/code/Mageplaza/HelloWorld/etc/frontend/routes.xml

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/etc/routes.xsd">
    <router id="standard">
        <route frontName="helloworld" id="helloworld">
            <module name="Mageplaza_HelloWorld"/>
        </route>
    </router>
</config>
```

## Step 2: Create controller file

File: app/code/Mageplaza/HelloWorld/Controller/Index/Index.php

```php
<?php
namespace Mageplaza\HelloWorld\Controller\Index;

class Index implements HttpGetActionInterface
{
	protected $_pageFactory;

	public function __construct(
		\Magento\Framework\View\Result\PageFactory $pageFactory)
	{
		$this->_pageFactory = $pageFactory;
	}

	public function execute()
	{
		return $this->_pageFactory->create();
	}
}
```

## Step 3: Create Layout file

File: app/code/Mageplaza/HelloWorld/view/frontend/layout/helloworld_index_index.xml

<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="1column" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <referenceContainer name="content">
        <block class="Mageplaza\HelloWorld\Block\Index" name="helloworld_index_index" template="Mageplaza_HelloWorld::index.phtml" />
    </referenceContainer>
</page>

## Step 4: Create Block file

File: app/code/Mageplaza/HelloWorld/Block/Index.php

```php
<?php
namespace Mageplaza\HelloWorld\Block;
class Index extends \Magento\Framework\View\Element\Template
{

}
```

## Step 5: Create template file

File: app/code/Mageplaza/HelloWorld/view/frontend/templates/index.phtml

```html
<h2>Welcome to Mageplaza.com</h2>
```

## Step 6: Flush Magento cache

## Step 7: Run a test

Let’s open browser and navigate to

`http://<yourhost.com>/helloworld/index/index`

or

`http://<yourhost.com>/helloworld/`

## Permission - ACL

There is a checking permission method in admin controller. Let’s take an example:

```php
protected function _isAllowed()
{
    return $this->_authorization->isAllowed('Magento_AdminNotification::show_list');
}
```

It will check the current user has right to access this action or not, learn more Admin ACL Access Control Lists

## Outros métodos de Controller

Forward method

_forward() protected function will edit the request to transfer it to another controller/action class. This will not change the request url. For example, we have 2 actions Forward and Hello World like this:

```php
namespace Mageplaza\HelloWorld\Controller\Test;
class Forward extends \Magento\Framework\App\Action\Action
{
	public function execute()
	{
		$this->_forward('hello');
	}
}
```

---------
Redirect method

This method will transfer to another controller/action class and also change the response header and the request url. With above example, if we replace _forward() method by this _redirect() method:

	$this->_redirect('*/*/hello');

Then after access from the url http://example.com/route_name/test/forward, the url will be change to http://example.com/route_name/test/hello and show the message Hello World! Welcome to Mageplaza.com on the screen.