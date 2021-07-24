# Criando um tema
- Ir até página app -> design -> frontend
- Criar pasta com o nome da empresa
- Dentro da pasta com o nome da empresa ficarão os temas
- Para cada tema, criar uma pasta
- Dentro da pasta é obrigatório que os arquivos registration.php e theme.xml estejam incluídos.

Exemplo de arquivo registration.php:

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

use Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(ComponentRegistrar::MODULE, 'frontend/Alura_Moda/tema_teste', __DIR__);

```
`Nota:` O segundo parâmetro `frontend/Alura_Moda/tema_teste` se refere a pasta onde ficarão as definições do tema.

Exemplo de arquivo theme.xml:

```php
<!--
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */
-->
<theme xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Config/etc/theme.xsd">
    <title>Alura Teste</title>
    <parent>Magento/luma</parent>
</theme>

```
`Nota:` <title> se refere ao nome que o tema terá no painel adm.