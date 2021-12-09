## Arquivo registration.php

```php
<?php

\Magento\Framework\Component\ComponentRegistrar::register(
    \Magento\Framework\Component\ComponentRegistrar::LANGUAGE,
    'fcamara_pt_br',
    __DIR__
);
```

Nota: Precisa estar tudo em minúsculo.

## Arquivo language.xml

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>pt_BR</code>
    <vendor>fcamara</vendor>
    <package>pt_BR</package>
    <use vendor="rafaelcg" package="pt_BR"/>
</language>
```

## Arquivo pt_BR.csv

"The gift card code couldn't be added. Verify your information and try again.","Não foi possível adicionar o código do cartão-presente. Verifique suas informações e tente novamente."
