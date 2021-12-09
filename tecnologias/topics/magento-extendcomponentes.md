## Como funciona

Todos os componentes herdam, em último nível, uma uiClass.

uiClass é um objeto com atributos e métodos.

## Exemplo de herança

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

Nesse caso, significa que o component `teste.js` herdará todos os atributos e métodos de uiClass.