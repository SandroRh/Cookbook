## Inserir JS Component em PHTML template - Notação Declarativa

Source: https://devdocs.magento.com/guides/v2.4/javascript-dev-guide/javascript/js_init.html

- Passos:
1. Definir o Javascript Component
2. Criar o Javascript Component
2. Inicializar o Javascript Component

### 1. Definir o Javascript Component

Adicionar o seguinte código em requirejs-config.js:
```js
var config = {
    map: {
        '*': {
                'carousel': 'js/carousel'
            }
        }
};

/**
* Onde:
* * = Seletor universal, seleciona o HTML DOM.
* 'carousel': 'js/carousel' = Define o componente de nome carousel e 
* indica o seu diretório. 
*/
```

### 2. Criar o Javascript Component

```js
require(['jquery', 'uiComponent'], function($, Component) {
    return Component.extend({
        name: this.name // Definido em text/x-magento-init
    });
})
```

### 3. Inicializar o Javascript Component

`Via text/x-magento-init tag`

Adicionar o seguinte código no arquivo .phtml:
```js
<script type="text/x-magento-init">
{
    "<selector>": {
        "<component>": <config>
    }
}
</script>
```

Exemplo:

```js
<script type="text/x-magento-init">
{
    "#teste": {
        carousel: {
            name: "Sandro" // Vai ser passado para o component js
        }
    }
}
</script>
```

