## Overview

A classe "\Magento\Framework\DataObject" é responsável por setar, adicionar ou pegar valores de objetos do Magento.

Pelo método **\Magento\Framework\DataObject::setData** podemos verificar quem está setando uma determinada informação.

## Recurso

https://www.youtube.com/watch?v=eo8N7e9eEPI

## Exemplos de uso

- 01: Quem está setando o filtro "LumaTech"?
- 02: Quem está setando o preço do produto "56.99"?
- 03: Quem está setando as "reviews"?

## Step-by-step

- Adicionar breakpoint em método setData.
- Adicionar condição como escrito abaixo (exemplo)
```php
stripos($value, '56.99') !== false
```


