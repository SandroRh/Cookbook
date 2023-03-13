# Passos

1. Adicionar javascript em requirejs-config.js
2. Criar javascript file

## Adicionar javascript em requirejs-config.js

Cada módulo possui um arquivo requirejs-config.js, seja um módulo de tema customizado (app/design) ou um módulo padrão (app/code). 

`Observações`:

Possíveis localizações:
- app/design/{Vendor}/{ModuleName}/requirejs-config.js
- app/code/{Vendor}/{ModuleName}/view/frontend/requirejs-config.js

File `app/code/Synapcom/TaxvatPayment/view/frontend/requirejs-config.js`

`Adição`:

```javascript
var config = {
    map: {
        '*': {
            'Magento_SalesRule/js/action/set-coupon-code':'Synapcom_TaxvatPayment/js/action/set-coupon-code'
        }
    },
};
```

## Criar javascript file

File `app/code/Synapcom/TaxvatPayment/view/frontend/web/js/action/set-coupon-code.js`

```javascript
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

/**
 * Customer store credit(balance) application
 */
define([
    'jquery',
], function (
    $,
) {
    'use strict';

    return function () {
        console.log("We get here");
    };
});
```