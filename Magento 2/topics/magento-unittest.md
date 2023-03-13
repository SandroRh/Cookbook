## Preparação de unit test

1. Copiar 4 arquivos e colar no modulo (pegar de algum repositório existente)
```
phpcs.xml.dist
Filephpmd.xml.dist
Filephpunit.xml
Filephpunit.xml.dist
```

2. Criar arquivo Test/Unit/bootstrap.php dentro do módulo
```php
<?php
/**
 * @author      Webjump Core Team <dev@webjump.com>
 * @copyright   2018 Webjump (http://www.webjump.com.br)
 * @license     http://www.webjump.com.br  Copyright
 *
 * @link        http://www.webjump.com.br
 */
// @codingStandardsIgnoreFile
require_once realpath(__DIR__.'/../../../../../../vendor/autoload.php'); // local
//require_once realpath(__DIR__.'/../../vendor/autoload.php'); // cloud
/**
 * @SuppressWarnings(PHPMD.ShortMethodName)
 */
if (!function_exists('__')) {
    function __()
    {
        $argc = func_get_args();

        $text = array_shift($argc);
        if (!empty($argc) && is_array($argc[0])) {
            $argc = $argc[0];
        }

        return new \Magento\Framework\Phrase($text, $argc);
    }
}
```
3. Rodar comando
```
./vendor/bin/phpunit -c app/code/Infracommerce/RewriteIntelipost/phpunit.xml.dist app/code/Infracommerce/RewriteIntelipost/
```

Esse comando gerará uma pasta chamada _Coverage dentro de `Test/Unit`

Após isso, entrar nessa pasta e abrir o index.html.