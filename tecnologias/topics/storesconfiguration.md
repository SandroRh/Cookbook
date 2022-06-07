# O que é

Stores -> Configuration se refere às configurações da loja.

## Documentação

https://www.mageplaza.com/magento-2-module-development/create-system-xml-configuration-magento-2.html

## Passo 1: Criar system.xml

The magento 2 system configuration page is divided logically in few parts: Tabs, Sections, Groups, Fields. Please check this images to understand about this:

![](./../assets/P8E2i4k.png)

Conteúdo de exemplo do system.xml:

`File: app/code/Mageplaza/HelloWorld/etc/adminhtml/system.xml`
```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="mageplaza" translate="label" sortOrder="10">
            <label>Mageplaza</label>
        </tab>
        <section id="helloworld" translate="label" sortOrder="130" showInDefault="1" showInWebsite="1" showInStore="1">
            <class>separator-top</class>
            <label>Hello World</label>
            <tab>mageplaza</tab>
            <resource>Mageplaza_HelloWorld::helloworld_config</resource>
            <group id="general" translate="label" type="text" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="0">
                <label>General Configuration</label>
                <field id="enable" translate="label" type="select" sortOrder="1" showInDefault="1" showInWebsite="0" showInStore="0">
                    <label>Module Enable</label>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>
                <field id="display_text" translate="label" type="text" sortOrder="1" showInDefault="1" showInWebsite="0" showInStore="0">
                    <label>Display Text</label>
                    <comment>This text will display on the frontend.</comment>
                </field>
            </group>
        </section>
    </system>
</config>
```

`Observações:`

1. `<resource></resource>` faz referência ao ACL.

## Passo 2: Setar valor default

Cada campo criado em system.xml inicialmente não terá nenhum valor. Quando você os chamar, você receberá null. Então precisamos setar o valor default.

`File: app/code/Mageplaza/HelloWorld/etc/config.xml`
```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <helloworld>
            <general>
                <enable>1</enable>
                <display_text>Hello World</display_text>
            </general>
        </helloworld>
    </default>
</config>
```
```xml
<default>
    <section>
        <group>
            <field>{value}</field>
        </group>
    </section>
</default>
```

## Passo 3: Flush magento cache

## Passo 4: Recupere o valor da configuração

Utilizamos o scopeConfig para recuperar os valores de configuração da loja.

O método getValue de scopeConfig possui 3 parâmetros:

`string $path`: O caminho da configuração. "section/group/field"

Exemplo: helloworld/general/enable

`string ScopeConfigInterface`: store ou default.

`null|int|string $scopeCode`: null por default. 

Helper file de exemplo:

`app/code/Mageplaza/HelloWorld/Helper/Data.php`

```php
<?php

namespace Mageplaza\HelloWorld\Helper;

use Magento\Framework\App\Helper\AbstractHelper;
use Magento\Framework\App\Config\ScopeConfigInterface $scopeConfig;
use Magento\Store\Model\ScopeInterface;

class Data extends AbstractHelper
{

	const XML_PATH_HELLOWORLD = 'helloworld/';

	public function getConfigValue($field, $storeId = null)
	{
		return $this->scopeConfig->getValue(
			$field, ScopeInterface::SCOPE_STORE, $storeId
		);
	}

	public function getGeneralConfig($code, $storeId = null)
	{

		return $this->getConfigValue(self::XML_PATH_HELLOWORLD .'general/'. $code, $storeId);
	}

}
```