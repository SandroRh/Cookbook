## Como fazer o setup de uma tabela no banco de dados

https://www.mageplaza.com/magento-2-module-development/how-to-create-crud-model-magento-2.html

`Tabela exemplo`: mageplaza_helloworld_post

    post_id - the post unique identifier
    name - the name of the post
    url_key - url of the post
    post_content - the content of the post
    tags - the tag of the post
    status - the status of the post
    featured_image - the image of the post
    created_at - the date created of the post
    updated_at - the date updated of the post

`app/code/Mageplaza/HelloWorld/Setup/InstallSchema.php`

```php
<?php
namespace Mageplaza\HelloWorld\Setup;

use Magento\Framework\Setup\UpgradeSchemaInterface;
use Magento\Framework\Setup\SchemaSetupInterface;
use Magento\Framework\Setup\ModuleContextInterface;

class UpgradeSchema implements UpgradeSchemaInterface
{
	public function upgrade( SchemaSetupInterface $setup, ModuleContextInterface $context ) {
		$installer = $setup;

		$installer->startSetup();

		if(version_compare($context->getVersion(), '1.1.0', '<')) {
			if (!$installer->tableExists('mageplaza_helloworld_post')) {
				$table = $installer->getConnection()->newTable(
					$installer->getTable('mageplaza_helloworld_post')
				)
					->addColumn(
						'post_id',
						\Magento\Framework\DB\Ddl\Table::TYPE_INTEGER,
						null,
						[
							'identity' => true,
							'nullable' => false,
							'primary'  => true,
							'unsigned' => true,
						],
						'Post ID'
					)
					->addColumn(
						'name',
						\Magento\Framework\DB\Ddl\Table::TYPE_TEXT,
						255,
						['nullable => false'],
						'Post Name'
					)
					->addColumn(
						'url_key',
						\Magento\Framework\DB\Ddl\Table::TYPE_TEXT,
						255,
						[],
						'Post URL Key'
					)
					->addColumn(
						'post_content',
						\Magento\Framework\DB\Ddl\Table::TYPE_TEXT,
						'64k',
						[],
						'Post Post Content'
					)
					->addColumn(
						'tags',
						\Magento\Framework\DB\Ddl\Table::TYPE_TEXT,
						255,
						[],
						'Post Tags'
					)
					->addColumn(
						'status',
						\Magento\Framework\DB\Ddl\Table::TYPE_INTEGER,
						1,
						[],
						'Post Status'
					)
					->addColumn(
						'featured_image',
						\Magento\Framework\DB\Ddl\Table::TYPE_TEXT,
						255,
						[],
						'Post Featured Image'
					)
					->addColumn(
						'created_at',
						\Magento\Framework\DB\Ddl\Table::TYPE_TIMESTAMP,
						null,
						['nullable' => false, 'default' => \Magento\Framework\DB\Ddl\Table::TIMESTAMP_INIT],
						'Created At'
					)->addColumn(
						'updated_at',
						\Magento\Framework\DB\Ddl\Table::TYPE_TIMESTAMP,
						null,
						['nullable' => false, 'default' => \Magento\Framework\DB\Ddl\Table::TIMESTAMP_INIT_UPDATE],
						'Updated At')
					->setComment('Post Table');
				$installer->getConnection()->createTable($table);

				$installer->getConnection()->addIndex(
					$installer->getTable('mageplaza_helloworld_post'),
					$setup->getIdxName(
						$installer->getTable('mageplaza_helloworld_post'),
						['name','url_key','post_content','tags','featured_image'],
						\Magento\Framework\DB\Adapter\AdapterInterface::INDEX_TYPE_FULLTEXT
					),
					['name','url_key','post_content','tags','featured_image'],
					\Magento\Framework\DB\Adapter\AdapterInterface::INDEX_TYPE_FULLTEXT
				);
			}
		}

		$installer->endSetup();
	}
}
```

This content is showing how the table created, you can edit it to make your own table. Please note that Magento will automatically run this file for the first time when installing the module. If you installed the module before, you will need to upgrade module and write the table create code to the UpgradeSchema.php in that folder and change attribute setup_version greater than current setup version in module.xml at app/code/Mageplaza/HelloWorld/etc/module.xml.

Contents would be:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Mageplaza_HelloWorld" setup_version="1.1.0">
    </module>
</config>
```