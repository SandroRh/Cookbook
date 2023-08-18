1. Ter a base da versão do magento que será trabalhada, pois dessa versão você precisará extrair a pasta bin e o app/etc/env.php

2. Instalar a versão base do magento para obter o arquivo app/etc/env.php. Você pode pular esse passo se já possuir o arquivo.

3. Adequar o arquivo /app/etc/env.php.

4. Rodar o composer install
    - Se autenticação for requerida, pegar chaves no magento marketplace.
    - Se for projeto do cloud, pegar o auth.json do cloud.

5. Aplicar as permissões de arquivos necessárias
    - chmod 777 -R .

6. Banco de dados
    - CREATE DATABASE magento;
    - mysql -u root -p magento < arquivo.sql
    - Ir na tabela core_config_data e alterar o endereço do elasticsearch, e as URLs web/unsecure/base_url e web/secure/base_url.
    - Alterar admin/url/custom_path se a loja possuir (para acessar o admin)
    - No arquivo env e no docker, utilizar usuário root no mysql.
    - Em app/etc/env.php o host é o nome do container do banco de dados (db no nosso caso)

7. Rodar o setup:upgrade

8. Rodar o setup:di:compile

9. Alterar o modo de deploy para developer (bin/magento deploy:mode:set developer)

## Possíveis erros

- NGINX - 403 Forbidden