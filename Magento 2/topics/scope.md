## O que é

O bind "scope" se refere ao componente que será utilizado. Veja o exemplo abaixo.

## Exemplo

```html
<li class="greet welcome" data-bind="scope: 'customer'">
    <span data-bind="text: customer().fullname ? $t('Welcome, %1!').replace('%1', customer().fullname) : 'Default welcome msg!'"></span>
</li>
```

```js
<script type="text/x-magento-init">
{
    "*": {
        "Magento_Ui/js/core/app": {
            "components": {
                "customer": {
                    "component": "Magento_Customer/js/view/customer"
                }
            }
        }
    }
}
</script>
```

No exemplo acima, o componente do li welcome é o customer. O módulo de customer está localizado em `"component": "Magento_Customer/js/view/customer"`.