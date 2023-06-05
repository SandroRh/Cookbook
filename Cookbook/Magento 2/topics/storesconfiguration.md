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
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="panini" translate="label" sortOrder="999">
            <label>Panini</label>
        </tab>
        <section id="kiosk_date" translate="label" sortOrder="130" showInDefault="1" showInWebsite="1" showInStore="1">
            <label>Kiosk Date</label>
            <tab>panini</tab>
            <resource>Panini_KioskDate::access</resource>
            <group id="general" translate="label" type="text" sortOrder="10" showInDefault="1" showInWebsite="1"
                   showInStore="0">
                <label>Module</label>
                <field id="enabled" translate="label" type="select" sortOrder="1" showInDefault="1" showInWebsite="1"
                       showInStore="0">
                    <label>Module Enable</label>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
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
                <enabled>1</enabled>
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

namespace Panini\KioskDate\Helper;

use Magento\Framework\App\Helper\AbstractHelper;
use Magento\Store\Model\ScopeInterface;

class Data extends AbstractHelper
{
    public const KIOSK_DATE_GENERAL_ENABLED = 'kiosk_date/general/enabled';

    /**
     * @param null $storeId
     * @return bool
     */
    public function isEnabled($storeId = null): bool
    {
        return (bool)$this->scopeConfig->getValue(self::KIOSK_DATE_GENERAL_ENABLED, ScopeInterface::SCOPE_STORE);
    }
}
```