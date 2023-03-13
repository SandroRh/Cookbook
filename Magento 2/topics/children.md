## O que são childrens

Todo componente js pode possuir childrens. Childrens são como filhos, que, por serem filhos, estão diretamente relacionados com os pais. 

Childrens podem ser acessados nos templates dos pais.

Exemplo:

```html
<!-- ko foreach: getRegion('estimation') -->
    <!-- ko template: getTemplate() --><!-- /ko -->
<!--/ko-->
```

estimation é um filho. Daí é possível recuperar seu template.