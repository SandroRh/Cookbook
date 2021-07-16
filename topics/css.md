# Como adicionar estilos

## 1. Na página web, criar pastas: css -> source

## 2. Criar estilos, com _ na frente do nome, por convenção.

1. Exemplo: _header.less

## 3. Comandos necessários
1. sudo bin/magento cache:flush
2. Apagar pastas necessárias:
var/view_preprocessed, var/cache, var/page_cache, pub/static
3. Documentação: https://devdocs.magento.com/guides/v2.4/howdoi/php/php_clear-dirs.html

# Nota(s)

Os temas criados a partir de temas já existentes, para substituir seus estilos, devemos criar um arquivo chamado _extend.less

Por exemplo, na época que tive essa aula, o meu tema estava sendo criado tendo como parent o Magento/blank.