https://www.mageplaza.com/magento-2-module-development/how-to-create-crud-model-magento-2.html#step-1-setup-script

## O que é Model

O Magento 2 utiliza o padrão arquitetural MVC, onde M é "Model". Classes de modelo são responsáveis por encapsular os dados do seu negócio.

## O que é Resource Model

Resource Model é o que representa um ou mais registros de uma tabela. 

Exemplo: Um Resource Model de um Model Order representa um registro da tabela de Order.

Um Resource Model é responsável por realizar as operações de CRUD.

## O que é Collection

Collection é um tipo de Resource Model responsável por representar vários registros de uma tabela.

## Como criar um Model

`app/code/Mageplaza/HelloWorld/Model/Post.php`

```php
<?php

namespace Mageplaza\HelloWorld\Model;

class Post extends \Magento\Framework\Model\AbstractModel implements \Magento\Framework\DataObject\IdentityInterface
{
	const CACHE_TAG = 'mageplaza_helloworld_post';

	protected $_cacheTag = 'mageplaza_helloworld_post';

	protected $_eventPrefix = 'mageplaza_helloworld_post';

	protected function _construct()
	{
		$this->_init('Mageplaza\HelloWorld\Model\ResourceModel\Post');
	}

	public function getIdentities()
	{
		return [self::CACHE_TAG . '_' . $this->getId()];
	}

	public function getDefaultValues()
	{
		$values = [];

		return $values;
	}
}
```

This model class will extends AbstractModel class Magento\Framework\Model\AbstractModel and implements \Magento\Framework\DataObject\IdentityInterface. The IdentityInterface will force Model class define the getIdentities() method which will return a unique id for the model. You must only use this interface if your model required cache clear after database operation and render information to the frontend page.

The _construct() method will be called whenever a model is instantiated. Every CRUD model have to use the _construct() method to call _init() method. This _init() method will define the resource model which will actually fetch the information from the database. As above, we define the resource model Mageplaza\Post\Model\ResourceModel\Post The last thing about model is some variable which you should you in your model:

## Como criar um Resource Model

```php
<?php
namespace Mageplaza\HelloWorld\Model\ResourceModel;


class Post extends \Magento\Framework\Model\ResourceModel\Db\AbstractDb
{
	
	public function __construct(
		\Magento\Framework\Model\ResourceModel\Db\Context $context
	) {
		parent::__construct($context);
	}
	
	protected function _construct()
	{
		$this->_init('mageplaza_helloworld_post', 'post_id');
	}
	
}
```

Every CRUD resource model in Magento must extends abstract class \Magento\Framework\Model\ResourceModel\Db\AbstractDb which contain the functions for fetching information from database.

Like model class, this resource model class will have required method _construct(). This method will call _init() function to define the table name and primary key for that table. In this example, we have table mageplaza_helloworld_post and the primary key post_id.

## Como criar uma Collection

`app/code/Mageplaza/HelloWorld/Model/ResourceModel/Post/Collection.php`

```php
<?php
namespace Mageplaza\HelloWorld\Model\ResourceModel\Post;

class Collection extends \Magento\Framework\Model\ResourceModel\Db\Collection\AbstractCollection
{
	protected $_idFieldName = 'post_id';
	protected $_eventPrefix = 'mageplaza_helloworld_post_collection';
	protected $_eventObject = 'post_collection';

	/**
	 * Define resource model
	 *
	 * @return void
	 */
	protected function _construct()
	{
		$this->_init('Mageplaza\HelloWorld\Model\Post', 'Mageplaza\HelloWorld\Model\ResourceModel\Post');
	}

}
```

The CRUD collection class must extends from \Magento\Framework\Model\ResourceModel\Db\Collection\AbstractCollection and call the _init() method to init the model, resource model in _construct() function.

