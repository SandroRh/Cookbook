# Como usar ícones

Esse guia explicará brevemente como utilizar ícones do próprio magento. 

Site de referência: https://magento-devdocs.github.io/magento2-ui-library/icons.html

## Font Icon

```css
.example-icon {
    .lib-icon-font(
        @icon-calendar,
        @_icon-font-size: 16px
    );
}
```

Em pseudo elements (:before e :after):
```css
&:after {
    font-family: 'luma-icons';
    content: '\e608';
    display: inline-block;
    font-size: 14px;
}
```

A lista de Font Icon está no site de referência.

## Sprite Icon

```css
.example-icon-7 {
    .lib-icon-image(@_icon-image: '@{baseDir}images/blank-theme-icons.png');
}
```

A lista de Sprite Icon está no site de referência.