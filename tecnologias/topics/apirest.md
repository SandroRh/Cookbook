# Como criar uma API Rest

## Passo 1: Criar webapi.xml em /etc

```xml
<?xml version="1.0"?>
<routes xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Webapi:etc/webapi.xsd">
    <route method="POST" url="/V1/custom/custom-api/">
        <service class="Meetanshi\CustomApi\Api\CustomInterface" method="getPost"/>
        <resources>
            <resource ref="anonymous"/>
        </resources>
    </route>
</routes>
```

Padrão de URL: `/V1/<nome_do_modulo>/<nome_da_acao>`

Onde: 

`<route></route>` define a url e o método.

`<service/>` define a class que receberá a requisição e o seu método.

`<resources>` indica quem poderá fazer a requisição
`ref` refere-se a uma ACL. Exemplo: Mundipagg_Module::core_customer_save

### Tokens: System -> Integrations
Obs: Talvez seja necessário criar uma ACL.

## Passo 2: Criar di.xml

```xml	
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <preference for="Meetanshi\CustomApi\Api\CustomInterface" type="Meetanshi\CustomApi\Model\Api\Custom"/>
</config>
```

## Passo 3: Criar interface em Api/NomeDaInterface

```php
<?php
 
namespace Meetanshi\CustomApi\Api;
 
interface CustomInterface
{
    /**
     * GET for Post api
     * @param string $value
     * @return string
     */
 
    public function getPost($value);
}
```

## Passo 4: Criar model em Model/Api/NomeDoModel

```php
<?php

namespace Panini\KioskDate\Model\Api;

use Panini\KioskDate\Api\DateChangeInterface;
use Psr\Log\LoggerInterface;

class DateChange implements DateChangeInterface
{
    /**
     * @var LoggerInterface
     */
    private LoggerInterface $logger;

    public function __construct(
        LoggerInterface $logger
    ) {
        $this->logger = $logger;
    }

    /**
     * @inheritdoc
     */
    public function getPost(int $storeCode, int $id)
    {
        $response = ['success' => false];

        try {
            // Your Code here

            $response = ['success' => true, 'message' => 'lalala'];
        } catch (\Exception $e) {
            $response = ['success' => false, 'message' => $e->getMessage()];
            $this->logger->info($e->getMessage());
        }

        return json_encode($response);
    }
}

```

### Passo 5: bin/magento se:up

### 6. Em caso de erros, verificar o checklist:
```
Service interfaces should be in Api folder.
Dto interfaces should be in Api/Data folder.
All interface methods should be type hinted. (Argument types, return types)
Imports should not be used. Specify a full namespace path for class.
ALL interfaces should have the correct PHPDOC.
```