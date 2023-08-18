## O que é Data Patch?
https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/

Data Patch é uma instrução que será executada apenas uma vez quando o comando setup:upgrade é executado. Para rodar novamente, é necessário excluir o registro da tabela "patch_list".

## Usage Guide

`Setup/Patch/Data/NomeDoArquivo.php`

```php
<?php

namespace Infobase\StoreData\Setup\Patch\Data;

use Infobase\StoreData\Setup\Installer;
use Magento\Framework\Setup;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;

/**
 * Class InstallCategories
 */
class InstallCategories implements DataPatchInterface
{
    /**
     * @var Setup\SampleData\Executor
     */
    protected Setup\SampleData\Executor $executor;

    /**
     * @var Installer
     */
    protected Installer $installer;

    /**
     * InstallCategories constructor.
     * @param Setup\SampleData\Executor $executor
     * @param Installer $installer
     */
    public function __construct(
        Setup\SampleData\Executor $executor,
        Installer $installer
    ) {
        $this->executor = $executor;
        $this->installer = $installer;
    }

    /**
     * {@inheritdoc}
     */
    public function apply()
    {
        $this->executor->exec($this->installer);
    }

    /**
     * {@inheritdoc}
     */
    public static function getDependencies()
    {
        return [];
    }

    /**
     * {@inheritdoc}
     */
    public function getAliases()
    {
        return [];
    }
}
```

## Exemplo: Criando um atributo de produto e adicionando em todos os attribute sets

```php
<?php

namespace Panini\Attributes\Setup\Patch\Data;

use Magento\Catalog\Model\Product;
use Magento\Eav\Setup\EavSetupFactory;
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;

class AddIsTaxedAttribute implements DataPatchInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private ModuleDataSetupInterface $moduleDataSetup;
    /**
     * @var EavSetupFactory
     */
    private EavSetupFactory $eavSetupFactory;

    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     * @param EavSetupFactory $eavSetupFactory
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup,
        EavSetupFactory $eavSetupFactory
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
        $this->eavSetupFactory = $eavSetupFactory;
    }

    /**
     * @inheritDoc
     */
    public static function getDependencies()
    {
        return [];
    }

    /**
     * @inheritDoc
     */
    public function apply()
    {
        $this->moduleDataSetup->getConnection()->startSetup();
        $eavSetup = $this->eavSetupFactory->create(['setup' => $this->moduleDataSetup]);

        $eavSetup->addAttribute(
            Product::ENTITY,
            'is_taxed',
            [
                'type' => 'int',
                'backend' => '',
                'frontend' => '',
                'label' => 'Is Taxed',
                'input' => 'boolean',
                'class' => '',
                'source' => 'Magento\Eav\Model\Entity\Attribute\Source\Boolean',
                'global' => \Magento\Eav\Model\Entity\Attribute\ScopedAttributeInterface::SCOPE_STORE,
                'visible' => true,
                'required' => false,
                'user_defined' => false,
                'default' => '0',
                'searchable' => false,
                'filterable' => true,
                'comparable' => false,
                'visible_on_front' => false,
                'used_in_product_listing' => false,
                'unique' => false
            ]
        );

        $entityTypeId = $eavSetup->getEntityTypeId(Product::ENTITY);
        $allAttributeSetIds = $eavSetup->getAllAttributeSetIds($entityTypeId);
        foreach ($allAttributeSetIds as $attributeSetId) {
            $groupId = $eavSetup->getAttributeGroupId($entityTypeId, $attributeSetId, 'General');
            $eavSetup->addAttributeToGroup(
                $entityTypeId,
                $attributeSetId,
                $groupId,
                'is_taxed'
            );
        }

        $this->moduleDataSetup->getConnection()->endSetup();
    }

    /**
     * @inheritDoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### Referência para atributos de produto
https://developer.adobe.com/commerce/php/development/components/attributes/#add-product-eav-attribute-options-reference