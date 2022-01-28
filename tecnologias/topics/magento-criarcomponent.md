# Como funciona um component no Magento 2

Recurso: [Clique aqui.](https://www.youtube.com/watch?v=Sz0XKqkn0cg)

O Magento 2 funciona a partir do padrão MVC. 

V - Layout, Block & Template. 

Um UiComponent é nada mais que o V do padrão.

Veja abaixo quais são os passos para a criação de um UiComponent.

## Passos

1. Inserir o block no layout
2. Inserir o template no block (dentro do layout)
3. Criar o template (phtml) e x-magento-init
4. Criar o viewModel (arquivo js)
5. Criar o outro template (html)

## 1. Inserir o block no layout

```xml
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        <referenceContainer name="content">
            <block class="Codilar\HelloWorld\Block\Hello" name="helloworld" template="Codilar_HelloWorld::hello.phtml" />
        </referenceContainer>
    </body>
</page>
```

## 2. Inserir o template no block (dentro do layout)

```xml
<block class="Codilar\HelloWorld\Block\Hello" name="helloworld" template="Codilar_HelloWorld::hello.phtml" />
```

## 3. Criar o template (phtml) e x-magento-init

Caminho: templates/hello.pntml

```php
<?php
/* @var Codilar\HelloWorld\Block\Hello $block */
?>
<div data-bind="scope: 'knockout-tutorial'">
    <!-- ko template: getTemplate() --><!-- /ko -->
</div>
<script type="text/x-magento-init">
    {
        "*": {
            "Magento_Ui/js/core/app": {
                "components": {
                    "knockout-tutorial": {
                        "component": "Codilar_HelloWorld/js/viewModel",
                        "template" : "Codilar_HelloWorld/nome"
                    }
                }
            }
        }
    }
</script>
```

Onde: 

`scope: 'knockout-tutorial'`: Define o escopo que será procurado. Uma espécie de nome.

`getTemplate()`: Vai procurar o template definido dentro do component.

`"*" : {`: * Faz referência a todos os elementos. Poderia ser "div" ou "#meuelemento".

`Magento_Ui/js/core/app`: Referência ao inicializador de componentes. Esse inicializador espera uma lista de componentes.

`components`: Espera um objetivo com uma lista de componentes.

`knockout-tutorial`: Escopo.

`component`: Arquivo JS localizado dentro de web/js.

`template`: Arquivo HTML localizado dentro de web/template.

## 4. Criar o viewModel (arquivo js)

```javascript
define([
    'uiComponent',
    'ko'
], function (Component, ko) {
    return Component.extend({
        number: ko.observable(0),
        sayHi: function () {
            return "Oi!";
        },
        getNumber: function () {
            return this.number;
        },
        incrementNumber: function () {
            this.number(this.number() + 1);
        }
    });
});
```

## 5. Criar o outro template (html)
```html
<h1 data-bind="text: getNumber()"></h1>

<button data-bind="click: incrementNumber">Click me</button>
```