# O que é a Access Control List (ACL)?

Access Control List é o sistema que o magento utiliza para limitar o nível de acesso de um usuário admin.

Pode ser acessado em: System -> Permission -> User Rules.

A imagem abaixo faz referência ao clique em "Add new role"
![](./../assets/jotYywG.png)

## Documentação

https://www.mageplaza.com/magento-2-module-development/magento-2-acl-access-control-lists.html

## Passo 1: Crie um cargo (role)

Para criar um cargo, precisamos atribuir ao cargo resources. Para criar resources, utilizamos o arquivo acl.xml.

`app/code/Mageplaza/HelloWorld/etc/acl.xml`
```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Acl/etc/acl.xsd">
    <acl>
        <resources>
            <resource id="Magento_Backend::admin">
                <resource id="Magento_Backend::stores">
                    <resource id="Magento_Backend::stores_settings">
                        <resource id="Magento_Config::config">
                            <resource id="Mageplaza_HelloWorld::helloworld_config" title="Hello World"/>
                        </resource>
                    </resource>
                </resource>
            </resource>
        </resources>
    </acl>
</config>
```

O resultado do código acima pode ser visto dentro de Stores -> Settings -> Configuration -> Hello World

## Passo 2: Flush Magento Cache