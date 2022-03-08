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

Onde: 

`<route></route>` define a url e o método.

`<service/>` define a class que receberá a requisição e o seu método.

`<resources>` indica quem poderá fazer a requisição.

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

namespace Meetanshi\CustomApi\Model\Api;

use Psr\Log\LoggerInterface;

class Custom implements CustomInterface
{
    protected $logger;

    public function __construct(
        LoggerInterface $logger
    )
    {

        $this->logger = $logger;
    }

    /**
     * @inheritdoc
     */

    public function getPost($value)
    {
        $response = ['success' => false];

        try {
            // Your Code here
            
            $response = ['success' => true, 'message' => $value];
        } catch (\Exception $e) {
            $response = ['success' => false, 'message' => $e->getMessage()];
            $this->logger->info($e->getMessage());
        }
        $returnArray = json_encode($response);
        return $returnArray; 
    }
}
```

### Passo 5: bin/magento se:up