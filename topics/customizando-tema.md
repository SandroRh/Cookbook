# Como customizar o tema de um módulo
- **Seguir todo o processo de criação de um tema**

- **Dentro da pasta do tema, criar uma pasta com o nome do componentName extraído do registration.php do módulo**

Exemplo: Customizar o module-theme
`componentName: Magento_Theme`

- **No caso, como queremos customizar o arquivo default.xml, precisamos descobrir onde ele está localizado no tema original (Magento_Theme). Após descobrir sua localização, ela deve ser replicada em nossa pasta.**

Vale ressaltar, que a pasta raiz do tema, a `Magento_Theme`, é equivalente a pasta `view/frontend` do tema original.

A réplica ficaria dessa forma: `Magento_Theme -> layout -> default.xml`

- **Copiar o arquivo default.xml do tema original e inserir na nossa customização**
- **Apagar todo o conteúdo e deixar apenas page**

Exemplo:
```php
<?xml version="1.0"?>
<!--
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */
-->
<page layout="3columns" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
   <referenceBlock name="logo">
       <arguments>
           <argument name="logo_width" xsi:type="number">150</argument>
           <argument name="logo_height" xsi:type="number">100</argument>
           <argument name="logo_file" xsi:type="string">web/images/logo.png</argument>
       </arguments>
   </referenceBlock>
</page>
```

Onde:
- logo_width foi extraído do bloco do logo, de getLogoWidth(), e os demais também.