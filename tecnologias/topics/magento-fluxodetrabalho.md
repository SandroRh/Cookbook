1. Ter a base da versão do magento que será trabalhada, pois dessa versão você precisará extrair a pasta bin e o app/etc/env.php
2. Instalar a versão base do magento para obter o arquivo app/etc/env.php. Você pode pular esse passo se já possuir o arquivo.
3. Adequar o arquivo /app/etc/env.php.
4. Rodar o composer install
5. Aplicar as permissões de arquivos necessárias
6. Puxar o banco de dados e as alterações necessárias, como: Ir na tabela core_config_data e alterar o endereço do elasticsearch (catalog/search/elasticsearch7_server_hostname), e as URLs (web/unsecure/base_url e web/secure/base_url)
7. Rodar o setup:upgrade
8. Rodar o setup:di:compile
9. Alterar o modo de deploy para developer