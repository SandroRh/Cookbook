# Como importar fontes

## 1. Adicionar fonte aos arquivos
A fonte deve ser adicionada em web/fonts.

`Exemplo:` web/fonts/Icomoon/Icomoon.woff

`Observação:` É importante que a fonte esteja em .woff ou .woff2, porque o Magento vai procurar por esses arquivos.

## 2. Adicionar fonte em _typography.less
O arquivo _typography.less vem do tema parente. Para descobrir qual é, verifique o arquivo theme.xml.

É necessário copiar todo o conteúdo desse arquivo quando for estendê-lo.

```css

// /**
//  * Copyright © Magento, Inc. All rights reserved.
//  * See COPYING.txt for license details.
//  */

//
//  Common
//  _____________________________________________

& when (@media-common = true) {
    .lib-font-face(
        @family-name: @font-family-name__base,
        @font-path: '@{baseDir}fonts/opensans/light/opensans-300',
        @font-weight: 300,
        @font-style: normal,
        @font-display: swap
    );

    .lib-font-face(
        @family-name: @font-family-name__base,
        @font-path: '@{baseDir}fonts/opensans/regular/opensans-400',
        @font-weight: 400,
        @font-style: normal,
        @font-display: swap
    );

    .lib-font-face(
        @family-name: @font-family-name__base,
        @font-path: '@{baseDir}fonts/opensans/semibold/opensans-600',
        @font-weight: 600,
        @font-style: normal,
        @font-display: swap
    );

    .lib-font-face(
        @family-name: @font-family-name__base,
        @font-path: '@{baseDir}fonts/opensans/bold/opensans-700',
        @font-weight: 700,
        @font-style: normal,
        @font-display: swap
    );

    .lib-font-face(
        @family-name:'Trade Gothic',
        @font-path: '@{baseDir}fonts/Trade-Gothic-W01/Trade-Gothic',
        @font-weight: 400,
        @font-style: normal
    );

    .lib-font-face(
        @family-name:'Icomoon',
        @font-path: '@{baseDir}fonts/Icomoon/Icomoon',
        @font-weight: 400,
        @font-style: normal
    );
}

//
//  Desktop
//  _____________________________________________

.media-width(@extremum, @break) when (@extremum = 'min') and (@break = @screen__m) {
    h1 {
        .lib-css(font-size, @h1__font-size-desktop);
        .lib-css(margin-bottom, @h1__margin-bottom__desktop);
    }
}

//
//  Common
//  _____________________________________________

& when (@media-common = true) {
    .items {
        .lib-list-reset-styles();
    }
}

```

No exemplo acima, foram adicionadas duas fontes: Trade Gothic e Icomoon.