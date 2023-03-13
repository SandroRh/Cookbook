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
class InstallCategories implements DataPatchInterface, PatchVersionInterface
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
    public static function getVersion()
    {
        return '1.0.0';
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