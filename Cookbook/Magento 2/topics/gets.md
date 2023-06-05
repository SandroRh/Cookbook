## getRegion

getRegion refere-se a uma seção específica definida como displayArea. Exemplo:

```js
"estimation": {
    "sortOrder": "10",
    "component": "Magento_Checkout/js/view/estimation",
    "displayArea": "estimation",
    "config": {
    "template": "Magento_Checkout/estimation",
    "deps": [
        "checkout.sidebar"
    ]
    }
}
```

```html
<!-- ko foreach: getRegion('estimation') -->
    <!-- ko template: getTemplate() --><!-- /ko -->
<!--/ko-->
```

## getRegion dentro de outra region

```html
<!-- ko foreach: getRegion('steps') -->
    <!-- ko foreach: getRegion('shipping-step') -->
        <!-- ko template: getTemplate() -->
        <!--/ko-->
    <!--/ko-->
<!--/ko-->
```

No exemplo acima, primeiro acessamos a region steps, dentro dessa region, existem outras regions, como a shipping-step, que não poderia ser acessada de fora.

## getTemplate

Todo módulo RequireJS pode possuir um template. Nesse caso, a diretiva:

```html
<!-- ko template: getTemplate() -->
```
é responsável por recuperar o conteúdo desse template. Os templates ficam em view/frontend/web/template.