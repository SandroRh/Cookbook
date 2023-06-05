## Source

https://alanstorm.com/the-curious-case-of-magento-2-mixins/

## O que são

Mixins funcionam como uma forma de herança. Veja o exemplo abaixo.

## Exemplo

```js
//File: app/code/Pulsestorm/RequireJsRewrite/view/base/requirejs-config.js
var config = {
    'config':{
        'mixins': {
            'Magento_Customer/js/view/customer': {
                'Pulsestorm_RequireJsRewrite/hook':true
            }
        }
    }
};    
```

```js
//File: app/code/Pulsestorm/RequireJsRewrite/view/base/web/hook.js
define([], function(){
    'use strict';    
    console.log("Called this Hook.");
    return function(targetModule){
        targetModule.crazyPropertyAddedHere = 'yes';
        return targetModule;
    };
});
```

No exemplo acima, o requireJS módulo `Magento_Customer/js/view/customer` receberá o conteúdo de `Pulestorm_RequireJsRewrite/hook`.

O mixin retorna uma função que será chamada após carregar um módulo do RequireJS. Essa função recebe apenas um parâmetro, o targetModule, que nesse caso, é o módulo customer.

É possível, portanto, acessar o `crazyPropertyAddedHere` através de (no console):

```js
> module = requirejs('Magento_Customer/js/view/customer');
> console.log(module.crazyPropertyAddedHere)
"yes"
```