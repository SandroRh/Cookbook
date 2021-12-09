## Anatomia

Componente: teste.js

```javascript
define(
    ['uiClass'], function(uiClass) {
        'use strict';

        return uiClass.extend({
            defaults: {
                "aaa": "aaa"
            },
        });
    }
);
```

- `['uiClass']`: Classes (js) que serão importadas.
- `function(uiClass)`: Apelido para a classe importada.
- `return uiClass.extend`: Deve retornar um objeto.
- `defaults:` Um objeto com os atributos padrões desse objeto, será, por exemplo, possivel acessar "aaa" com this.aaa.