# Passos
## 1. Descubra qual o block do elemento
## 2. Decida para qual container você quer enviá-lo
## 3. Crie a customização do layout
## 4. Código exemplo para mover elementos
```php
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <move element="authorization-link" destination="header-wrapper"></move>
</page>
``` 

Onde: `authorizathion-link` é o name do block, e `header-wrapper` é o container.

# Atributos de \<move>
`before="-"`: Indica que o elemento deve ser colocado antes de todos no container.
`after="nome"`: Indica que o elemento deve ser colocado após o bloco nome.