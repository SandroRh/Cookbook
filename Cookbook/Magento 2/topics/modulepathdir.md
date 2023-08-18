```php
use Magento\Framework\Module\Dir\Reader;

public function __construct(
    Reader $moduleDirectory
) {
    $this->moduleDirectory = $moduleDirectory;
}

$etcDir = $this->moduleDirectory->getModuleDir(
    Dir::MODULE_ETC_DIR,
    'Panini_Correios'
);

$filePath = $etcDir . '/correios/correios_codes.csv';
```