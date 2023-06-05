## Como funciona

O exemplo descrito abaixo é referente a uma forma que eu encontrei de renderizar qualquer elemento filho. Aparentemente, o getRegion funciona apenas para os primeiros filhos de um componente js.

## Exemplo

onepage.js
```javascript
define([
        'ko',
        'jquery',
        'uiRegistry',
        'uiComponent',
        'Magento_Checkout/js/model/quote'
    ], function(ko, $, Registry, Component, quote) {
        'use strict';
        return Component.extend({
            getShippingStep: function() {
                var shippingStep = Registry.get('checkout').getRegion('steps')()[0].elems()[0];
                return shippingStep;
            },

            getBillingStep: function() {
                var billingStep = Registry.get('checkout').getRegion('steps')()[0].elems()[1];
                return billingStep;
            }
        });
    }
);
```

onepage.html
```html
<!-- ko with: getShippingStep() -->
<!-- ko template: getTemplate() -->
<!--/ko-->
<!--/ko-->
```

Debug no console:
```js
Registry = requirejs("uiRegistry");
shippingStep = Registry.get('checkout').getRegion('steps')()[0].elems()[0];
```