Observe o arquivo:
```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Console\CommandListInterface">
        <arguments>
            <argument name="commands" xsi:type="array">
                <item name="import_customer" xsi:type="object">Infobase\ImportCustomer\Console\Command\ImportCustomer</item>
            </argument>
        </arguments>
    </type>
</config>
```

O que é feito aqui, é que passamos para o construtor da classe CommandListInterface, dentro do argumento commands, um item chamado "import_customer". Dessa forma, inserimos um novo comando no Magento, sem precisar alterar os arquivos originais.

## Uma outra abordagem

Uma outra possível abordagem é a de um teste que tive de desenvolver, o caso dos profiles. 

O usuário poderia escolher entre dois profiles: sample-csv e sample-json, porém, um dos requisitos era que o módulo devia estar aberto para expansão de profiles sem que fosse necessário alterar os arquivos originais.

No meu entendimento, o ideal seria criar uma classe que recebe um array de profiles no construtor, e para esse construtor, utilizar a mesma abordagem de acima, colocando os itens via dependency injection.
