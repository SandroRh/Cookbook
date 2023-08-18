Instalação
==========

- Ter a base da versão do magento que será trabalhada, pois dessa versão você precisará extrair a pasta bin e o app/etc/env.php

- Instalar a versão base do magento para obter o arquivo app/etc/env.php. Você pode pular esse passo se já possuir o arquivo.

- Adequar o arquivo /app/etc/env.php.

- Rodar o composer install
    - Se autenticação for requerida, pegar chaves no magento marketplace.
    - Se for projeto do cloud, pegar o auth.json do cloud.

- Banco de dados
    - CREATE DATABASE magento;
    - mysql -u root -p magento < arquivo.sql
    - Ir na tabela core_config_data e alterar o endereço do elasticsearch, e as URLs web/unsecure/base_url e web/secure/base_url.
    - Alterar admin/url/custom_path se a loja possuir (para acessar o admin)
    - No arquivo env e no docker, utilizar usuário root no mysql.
    - Em app/etc/env.php o host é o nome do container do banco de dados (db no nosso caso)

```sql
UPDATE core_config_data SET value = "localhost" WHERE path = "web/cookie/cookie_domain";
UPDATE core_config_data SET value = "http://localhost/" WHERE path = "web/unsecure/base_link_url";
UPDATE core_config_data SET value = "http://localhost/" WHERE path = "web/secure/base_link_url";
```

- Rodar o setup:upgrade

- Rodar o setup:di:compile

- Alterar o modo de deploy para developer (bin/magento deploy:mode:set developer)

- Aplicar as permissões de arquivos necessárias
    - chmod 777 -R .